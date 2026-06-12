---
title: "Is there a repository of source click packages for Ubuntu touch?"
date: 2016-04-05
forum: Ubuntu Phone and Tablet
---

### Post by ales-horak on 2016-04-05
I would like to take inspiration from looking at the source code of several Ubuntu touch applications installed in my BQ 4.5 phone. Is there a way how to find and download the source code of applications from the Ubuntu Store?

---

### Post by krusty8 on 2016-04-11
For all the apps that I have looked at, the url given in the store points to their launchpad site.
E.g. 
[LIST]
[*]go here [https://uappexplorer.com/app/talaan.kugiigi](https://uappexplorer.com/app/talaan.kugiigi) 
[*]click on support 
[*]click on the link 
[*]click on Code 
[*]click on browse 
[*]end up here [http://bazaar.launchpad.net/~kugi-igi/talaan-app/trunk/files](http://bazaar.launchpad.net/~kugi-igi/talaan-app/trunk/files) 
[/LIST]

---

### Post by ales-horak on 2016-04-12
well, but this does not hold for all packages. First, afaik uapp is not the Ubuntu store, it is an unofficial package list viewer. And second, the support URL in it does not always link to the launchpad site, see e.g. [https://uappexplorer.com/app/rssreaderscope.kazord](https://uappexplorer.com/app/rssreaderscope.kazord)

So far, the information nearest to what I am looking for is found in [https://wiki.ubuntu.com/AppStore/Interfaces/ClickPackageIndex](https://wiki.ubuntu.com/AppStore/Interfaces/ClickPackageIndex). E.g. I can:```
export ARCH=armhf
curl -s -H "X-Ubuntu-Architecture: $ARCH" -H 'Accept: application/hal+json' \
'https://search.apps.ubuntu.com/api/v1/search?q=rssreader' \
| jq '._embedded["clickindex:package"]'|grep href.*rssreaderscope
``` and obtain ```
"href": "https://search.apps.ubuntu.com/api/v1/package/rssreaderscope.kazord"
```
Then ```
curl -s -H "X-Ubuntu-Architecture: $ARCH" -H 'Accept: application/hal+json' \
'https://search.apps.ubuntu.com/api/v1/package/rssreaderscope.kazord' | jq '.'
```
gives all the package details including the link to the click package ```
"download_url": "https://public.apps.ubuntu.com/download/kazord/rssreaderscope.kazord/rssreaderscope.kazord_0.5.0_armhf.click"
``` but no link to the source repository or a source package.

---

### Post by krusty8 on 2016-04-18
> **ales-horak said:**
> well, but this does not hold for all packages. 
Correct.

> 
First, afaik uapp is not the Ubuntu store, it is an unofficial package list viewer.
Correct. It's an unofficial *viewer.* The *data* that is being viewed should be official though. 

> 
 And second, the support URL in it does not always link to the launchpad site, see e.g. [URL="https://uappexplorer.com/app/rssreaderscope.kazord"]https://uappexplorer.com/app/rssreaderscope.kazord
[/URL]
That app is listed with license: Proprietary. So I assume that they won't show you their sources.

---

