# Andrew's Note

August 21, 2024

Thank goodness for templates! Thanks to the folks at academicpages.github.io for making it easy (and free) to set up a personal website.

Here's a shortcut to my page at [wengandrew.github.io](https://wengandrew.github.io).

I'll write down some thoughts to hopefully help the next person who stumbles onto this page.
So you're here on the GitHub page. What do you do? Here's what I did.

## Follow "Getting Started"

See the blurb from the original README file below. Pay attention to the repository name!

## What is 'site-wide' configuration?

What this means is you need to go ahead and modify the file `_config.yml`. You'll need to at least update the 'url' and 'repository' fields in order for your webpage to show up. After you commit the changes, you can navigate to the "Actions" tab to see how GitHub is working to deploy the changes to the site. If all goes well, you'll be able to see your website at the designated URL. 

## A note about developing the code

Technically, you don't need to ever `git clone` and do things locally. The downside to doing things this way is that GitHub Actions takes around 1 minute to deploy each build, meaning each small update you make in the code will take some time to show up on the webpage. A slightly better option is to use GitHub Codespaces to open up an online instance of VSCode and develop the code there. This is marginally better than doing things on GitHub directly. Finally, the best way to do this is to develop locally. There are instructions for how to do this. I couldn't get my installer to work on my MacOSX due to some `brew` issues which I'll have to fix later.

## Make incremental updates and commit often. 

I went ahead and updated some more biographic information and URLs to my Google Scholar and ORCID. I committed these changes and waited a bit to see the changes on the website. This is a bit slow compared to developing things locally, but I am a simple person.

## Set up the "tabs" (pages) of your website.

The first thing to know is that `_data/navigation.yml` defines the top-level tabs that are visible from the main website. The file is pretty self-explanatory. Add and delete content as you please. Note that deleting content is easy. But if you want to add a new tab (technically called a "page"), how do you put content in here? See the next bullet point. 

## Updating content in each page

You have to know a bit about HTML and Markdown. Basically, these are two languages for putting and formatting content into a page. HTML is more expressive and can help you procedurally generate content in pages. Markdown is simpler and better for simple pages where all you need to do is type some text, and maybe some headers, plus some images. You'll find that the template uses a combination of HTML and Markdown pages. I would suggest starting with creating a tab using Markdown only. It's the fastest way to get started. All you have to do is go to `_pages/`, create a new `.md` file, and follow the existing `.md` files to set up the right header in this file. The important element here is the permalink field. This field must match what you specified in `_data/navigation.yml`. It basically tells your code that this is the file that links to the page specified in `navigation.yml`.

## Handling the publications page: a bit tricky

You have to first decide whether to manually maintain a simple .md file or go with the procedurally generated HTML page which automatically searches for individual .md files, each file holding information for a single publication. In the former case, you'll have to manually type everything out. In the latter case, it is also tedius to manually add an `.md` file for each publication (under `_publications`.), though this option gives you more flexibility for letting users 'click into' each publication, where you can provide a space to further describe that research (as part of the individual `.md` files). There are tools to help with this. For example, if you have a `.bib` file with all of your publications, there are some Python scripts to help you convert this `.bib` file to a set of `.md` files. I don't even know how this works yet. 

In any case, if you go the HTML route, another helpful tip is that the exact content that shows up under each publication is customizable. For example, you might notice that the default view doesn't have the author fields. This was pretty problematic to me. The solution was to open and update `_includes/archive-single.html`. This HTML file specifies the content and format for each publication. You can read through it and compare the fields on the webpage to get a gist of how each page element is being specific in the HTML language.

That's it for now. The rest of this README file is from the source.

---

# Academic Pages

![pages-build-deployment](https://github.com/academicpages/academicpages.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)

Academic Pages is a Github Pages template for academic websites.

# Getting Started

1. Register a GitHub account if you don't have one and confirm your e-mail (required!)
1. Click the "Use this template" button in the top right.
1. On the "New repository" page, enter your repository name as "[your GitHub username].github.io", which will also be your website's URL.
1. Set site-wide configuration and add your content.
1. Upload any files (like PDFs, .zip files, etc.) to the `files/` directory. They will appear at https://[your GitHub username].github.io/files/example.pdf.
1. Check status by going to the repository settings, in the "GitHub pages" section
1. (Optional) Use the Jupyter notebooks or python scripts in the `markdown_generator` folder to generate markdown files for publications and talks from a TSV file.

See more info at https://academicpages.github.io/

## Running Locally

When you are initially working your website, it is very useful to be able to preview the changes locally before pushing them to GitHub. To work locally you will need to:

1. Clone the repository and made updates as detailed above.
1. Make sure you have ruby-dev, bundler, and nodejs installed
    
    On most Linux distribution and [Windows Subsystem Linux](https://learn.microsoft.com/en-us/windows/wsl/about) the command is:
    ```bash
    sudo apt install ruby-dev ruby-bundler nodejs
    ```
    On MacOS the commands are:
    ```bash
    brew install ruby
    brew install node
    gem install bundler
    ```
1. Run `bundle install` to install ruby dependencies. If you get errors, delete Gemfile.lock and try again.
1. Run `jekyll serve -l -H localhost` to generate the HTML and serve it from `localhost:4000` the local server will automatically rebuild and refresh the pages on change.

If you are running on Linux it may be necessary to install some additional dependencies prior to being able to run locally: `sudo apt install build-essential gcc make`

# Maintenance

Bug reports and feature requests to the template should be [submitted via GitHub](https://github.com/academicpages/academicpages.github.io/issues/new/choose). For questions concerning how to style the template, please feel free to start a [new discussion on GitHub](https://github.com/academicpages/academicpages.github.io/discussions).

This repository was forked (then detached) by [Stuart Geiger](https://github.com/staeiou) from the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/), which is © 2016 Michael Rose and released under the MIT License (see LICENSE.md). It is currently being maintained by [Robert Zupko](https://github.com/rjzupkoii) and additional maintainers would be welcomed.

## Bugfixes and enhancements

If you have bugfixes and enhancements that you would like to submit as a pull request, you will need to [fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) this repository as opposed to using it as a template. This will also allow you to [synchronize your copy](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) of template to your fork as well.

Unfortunately, one logistical issue with a template theme like Academic Pages that makes it a little tricky to get bug fixes and updates to the core theme. If you use this template and customize it, you will probably get merge conflicts if you attempt to synchronize. If you want to save your various .yml configuration files and markdown files, you can delete the repository and fork it again. Or you can manually patch.
