---
title: "Unofficial Snap Packaging for Tidy: HTML parser and pretty printer"
date: 2018-08-22
forum: Ubuntu, Linux and OS Chat
---

### Post by buo-ren-lin on 2018-08-22
After days of development and testing, I am thrilled to announce that the unofficial packaging work of Tidy has finally reached its end.

[https://snapcraft.io/tidy-brlin](https://snapcraft.io/tidy-brlin)

[Tidy, or HTML Tidy]([http://www.html-tidy.org](http://www.html-tidy.org)), is an HTML parser, validator and pretty printer developed by Dave Raggett et. al., it can validate HTML/XML documents and beautify it with fine-grained customization options.

The main motivation of packaging Tidy as a snap is that the version shipped in Ubuntu 16.04 is a very old legacy version dated in late 2009, the application has been greatly improved since then and even uses a different version scheme and SCM system.  This snap provides the latest official and development(next) release of the `tidy` command-line utility in the stable and beta channels.

We are now in the process of contributing this work back to the upstream, [stay tuned]([https://github.com/htacg/tidy-html5/issues/748](https://github.com/htacg/tidy-html5/issues/748)) for more updates!

### How to Install ###
```
# Install Snap #
sudo snap install tidy-brlin

# Connect the Snap to Optional Interfaces #
## removable-media: For accessing files under `/media/*` and `/run/media/*`
sudo snap connect tidy-brlin:removable-media

```

### Related Links ###
* Packaging recipe source code  
  [https://github.com/Lin-Buo-Ren/tidy-snap](https://github.com/Lin-Buo-Ren/tidy-snap)
* Upstream project  
  [http://html-tidy.org](http://html-tidy.org)

### Support ###
Please refer our project's issue tracker  
[https://github.com/Lin-Buo-Ren/tidy-snap/issues](https://github.com/Lin-Buo-Ren/tidy-snap/issues)

or create a new topic under `snap` category in the Snapcraft Forums  
[https://forum.snapcraft.io](https://forum.snapcraft.io)

### Join Snapcrafters ###
[https://forum.snapcraft.io/t/join-snapcrafters/1325](https://forum.snapcraft.io/t/join-snapcrafters/1325)

---

### Post by oldos2er on 2018-08-22
Closed pending staff review.

---

