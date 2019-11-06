# GudangAda

GudangAda sales web apps powered by [Nuxt.js](https://nuxtjs.org).

## Setup Project

There are some requirement to setup environment for this project;

1. Install nvm & node v10.15.0 ([check this tutorial](http://dev.topheman.com/install-nvm-with-homebrew-to-use-multiple-versions-of-node-and-iojs-easily/))
2. Make sure `node --version` output is `v10.15.0`
3. Clone project
   ```bash
   git clone https://github.com/gudangada/gadasales.git
   ```
4. Enter project directory `cd gadasales` then execute `yarn` to install node dependencies.
5. Make `.env` with variable according to `example.env`
6. To begin local development execute `yarn run dev`
7. If need to add any `node_module` discuss in FE GaDa group.

## Start Development & Build Production App

```bash
# serve with hot reload at localhost:3000 and start develop
$ yarn run dev

# build for production and launch app as SSR
$ yarn run build
$ yarn start

# generate static production app 
$ yarn run generate
```

## Develop Feature
Developing and managing new features mainly we use pivotal task & some using github issues. To start develop read seaction below.

### Create new branch for new task
Read carefully your pivotal task story, if you're not soure about something ask the task owner / team leader
On your project directory do these
```bash
# To make sure all code updates
git fetch origin 

# Change to production branch or staging (if app haven't released yet)
git checkout master

# Make another branch based on production codebase
# then give the new branch name with this convention
# "<feature/chore/bug>/task-short-title-<pivotalID without hastag>"
git checkout -b feature/buyer-home-page-165672404
```

Please do best practice vuejs coding as describe here https://vuejs.org/v2/style-guide

### Development Tools
Our main text editor for coding is [Microsoft Visual Studio Code](https://code.visualstudio.com/download) please use it.
Then install and use some recomended extensions here:
- Best practice following [VueJS style guide](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
- [Prettify](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) your code automatically
- Really [do comment](https://marketplace.visualstudio.com/items?itemName=joelday.docthis) your js code please

I use another extension mention [here](https://github.com/azulkipli/vscode-nuazul)
If you need more go to [https://marketplace.visualstudio.com/vscode](https://marketplace.visualstudio.com/vscode)

### Test code & Audit page performance

While you develop features, fix bugs or any other, please always do audit page performance & unit test.

#### Unit test
If you have create unit test please run it, improve what you can add unit test.
```bash
yarn run test
```
#### Audit page performance
If you have created/updated pages, Please inspect, analyze, and throttle test speed (3G slow) each of pages with lighthouse.

To do that on localhost install [http-server-pwa](https://www.npmjs.com/package/http-server-pwa) 

Currenty in production we use `spa` mode so execute run `yarn run generate` 

Then serve static files `pwa-server build -p 9191 -s --ssl`

Run [lighthouse audit](https://developers.google.com/web/tools/lighthouse/#devtools) on your web browser.

Still not sure how to do lighthouse audit, [watch this video](https://www.youtube.com/watch?v=Y5XX2lruhxs)

Better you can do lighthouse audit test on netlify hosting (on your own account).

Improve performance section item best you can do.

Post the result (JSON export file & screenshot) and the reason why the improvement got that result to pivotal tracker task & github pull request.

### Merge code to staging or release branch
When you've done with you're work that need to merge code, please create [github Pull Request (PR)](https://github.com/gudangada/gadasales/compare).

1) when finished task and make new PR to staging / merge-buyer branch please do these;
    - insert pivotal task ID (linked as new tab) on github comment
    - write changelog summary, insert screenshot preview if needed on github comment
    - attach lighthouse audit screenshot & json report on github comment
    - add comment on pivotal task with latest changelog & lighthouse audit
    - on pivotal task assign QA review & Code review
    - on github PR ask code review to coordinator & team lead
2) when revision done recheck all list above and make new PR to staging / merge-buyer branch
3) add pivotal task to release flagged task with format <#ID> <enter/return> <Task title>, if release flagged task not exist yet ask team lead
4) when you working on PR please add useful info such as [WIP](https://github.com/apps/wip) / :construction: on title, label it if has same branch PR but to    different codebase.
5) when task accepted recheck all list above and make new PR to release branch (no need yet for app haven't been released)

   

#### PR to Staging
Select `staging` as **base** and you're branch as **compare** , click **Create pull request**
If your PR have no conflict you may merge it, but please notify team member because it will build staging app automatically.
If there are some conflict on merging please fix that with these steps,
On your local project directory
```
# To make sure all code updates
git fetch origin 

# Change to staging codebase
git checkout staging

# Merge you're branch into staging
git pull origin feature/buyer-home-page-165672404

# If any conflict solved it in this state then commit it
# Ask code review to other team member or leader
```

#### PR to Release
Select `release` as **base** and you're branch as **compare** , click **Create pull request**
If there are some conflict on merging please fix that with these steps,
On your local project directory
```
# To make sure all code updates
git fetch origin 

# Change to release codebase
git checkout release

# Merge you're branch into release
git pull origin feature/buyer-home-page-165672404

# If any conflict solved it in this state then commit it
# Ask code review to other team leader
# Let your team lead merge it
```
