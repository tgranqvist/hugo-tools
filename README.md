# Hugo tools

This is my basic setup for usig [Hugo][hugo] with [VS Code][vscode]. It is somewhat opinionated, suiting my needs.

- Site source code is in `src` subfolder
- Source in one (private) repo, publish to another
- Shortcuts as VS Code tasks

It should be fairly easy to extend the deployment workflow and/or add tasks.

## Using the tool

Easiest way is to run with NPX:

```shell
npx degit 
```

## Workflow

The workflow is based on the idea that the site source code is in one repository, perhaps a private one. On push,
the workflow builds and publishes the site using some awesome actions maybe by [peaceiris]:

- [GitHub Actions for Hugo][gah] - to build the site
- [GitHub Actions for GitHub Pages][gagp] - to publish the site

### Configuration

In your *source repo*, set the following values. You use the repo [variables] and [secrets] for this.

- DEPLOY_KEY, the private part of an [SSH deploy keypair][ssh]. This is a **secret**.
- TARGET_REPO, the repo to publish the built page to. This is a **variable**.
- SITE_CNAME, the cname value (domain name) for the site. This is a **variable**.

In the *target repo*, set the public part of the deploy key as a deploy key with write access.

## VS Code tasks

For convenience, I wanted some shortcuts for creating content and running the site. These are [VS Code tasks][tasks].

### New content

From the Terminal menu, select `Run Task ...` > `New post` > Give a page name. The post is created in src/content/posts
and opened in VS Code. The front matter is filled in.

[hugo]: https://gohugo.io/
[vscode]: https://code.visualstudio.com
[peaceiris]: https://github.com/peaceiris
[gah]: https://github.com/peaceiris/actions-hugo
[gagp]: https://github.com/peaceiris/actions-gh-pages
[variables]: https://docs.github.com/en/actions/learn-github-actions/variables
[secrets]: https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions
[ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys
[tasks]: https://code.visualstudio.com/Docs/editor/tasks
