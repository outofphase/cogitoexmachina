# README

This repository holds the current contents and some future drafts of the [cogito ex machina](https://outofphase.github.io/cogitoexmachina/) website.

The website records my investigations into Artificial General Intelligence, and is part notes and part blog.

## Contributing to the project

```
You must own the copyright to any material that you add, unless you give a clear attribution to the source and its usage falls under accepted 'fair use' exemptions. 

This project is published under the CC BY license, please don't submit any material unless you are prepared to have it published under those terms. See LICENSE.md for more details.
```

The entire site content is static HTML generated from Markdown text files. The HTML output and site infrastructure is created by the **mkdocs** program and served using **GitHub Pages**.

The source Markdown text files and some metadata is held in GitHub, with two branches:

* **published** &ndash; contains the source for the current live site
* **beta** &ndash; contains the source of the next release that is being integrated and tested.

Individual changes are generally made in sub-branches from the Draft branch, such as **alpha**.

### To update content on an existing page

Fork the repository on GitHub and modify the file or files then submit a Pull Request. I will check and integrate the changes and publish the updated site.

### To add a new page

Fork the repository on GitHub and add the file or files then submit a Pull Request. I will check and integrate the changes and publish the updated site.

### To fix the existing site structure

Fork the repository on GitHub and modify the directory structure and/or `mkdoc.yml` then submit a Pull Request. I will check and integrate the change and publish the updated site.

### To build a local copy of the whole site (if desired, but not necessary to contribute)

CIone the respository from GitHub.

Install `mkdocs` and read about it on the [**mkdocs** site](https://www.mkdocs.org/).

Run the `mkindex.sh`script to generate `docs/index.md` from the contents of `homepage/`.

Run `mkdocs build` to generate the site and `mkdocs serve` to test the site on `http://127.0.0.1:8000/`.

### To add a blog post

If the post is short and will not be shown in the **Latest** list on the home page then it can be added directly to the `docs/opinion/posts.md` file.

Otherwise, if the post is longer or will be shown on the home page then:

* Create the post as a markdown file in `docs/opinion/`. The post should start with title as H3 followed by full date in _italics_. The filename should start with the date in YYYYMMDD format.

* Copy then Paste all or part of the post to the `docs/opinion/posts.md` file. If only a part of the post is used then include a relative link to the full post using "Read more...". Separate the posts with a horizontal line.

* Normally the new post should be shown in the **Latest** list on the home page, so add a symbolic link to the new file in `homepage/`, with the link name defining the post's position in the list. Then run `./mkindex.sh`. Leave the header file `index.0.md` untouched but shuffle the remaining links down to put most recent entry at the top (pruning last entry if desired):

```bash
david@penguin:~/Sites/cogitoexmachina$ cd homepage/
david@penguin:~/Sites/cogitoexmachina/homepage$ ls -l
total 12
-rw-r--r-- 1 david david 530 Jan  1 14:29 index.0.md
lrwxrwxrwx 1 david david  34 Jan  1 16:24 index.1.md -> ../docs/opinion/20190101_pinker.md
lrwxrwxrwx 1 david david  38 Jan  1 12:24 index.2.md -> ../docs/opinion/20181230_first_post.md
david@penguin:~/Sites/cogitoexmachina/homepage$ mv index.2.md index.3.md
david@penguin:~/Sites/cogitoexmachina/homepage$ mv index.1.md index.2.md
david@penguin:~/Sites/cogitoexmachina/homepage$ ln -s ../docs/newpost.md index.1.md
david@penguin:~/Sites/cogitoexmachina/homepage$ ls -l
total 16
-rw-r--r-- 1 david david 530 Jan  1 14:29 index.0.md
lrwxrwxrwx 1 david david  18 Jan  1 16:36 index.1.md -> ../docs/newpost.md
lrwxrwxrwx 1 david david  34 Jan  1 16:24 index.2.md -> ../docs/opinion/20190101_pinker.md
lrwxrwxrwx 1 david david  38 Jan  1 12:24 index.3.md -> ../docs/opinion/20181230_first_post.md
```

> Note that the post markdown file should end with a newline character so that the Latest list is generated correctly.

### To add a review

Similar to adding a blog post (see above) but the review markdown file is saved in `docs/research/`and the summary file is `docs/research/reviews.md`.

Reviews can start small and have detail added over time. Generally only the most significant will be cross-posted to the **Latest** list on the home page.

