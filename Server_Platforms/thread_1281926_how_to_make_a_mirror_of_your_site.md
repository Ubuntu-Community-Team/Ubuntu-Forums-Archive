---
title: "how to make a mirror of your site"
date: 2009-10-03
forum: Server Platforms
---

### Post by coller_girl on 2009-10-03
so, ever needed to make a mirror of your site??? wondered how??? there is a way of using wget that ignores the robots file to make a new mirror its really easy too

just type

wget -e robots=off --mirror --random-wait --user-agent="Mozilla/5.0 (X11; U; Linux i686; pl-PL; rv:1.9.0.2) Gecko/20121223 Ubuntu/9.25 (jaunty) Firefox/3.8" [http://nameofsite.com/](http://nameofsite.com/)

so long as it is HTML it should make a file with the structure of your site  this could theoretically be used to check for open directories - a possible security issue...

(tip: doing this to try downloading google to your 160gb hdd is a BAD idea besides it is java script so... wont work after the first page)

---

### Post by SoftwareExplorer on 2009-10-04
Does this get files that have no links to them anywhere else?

---

