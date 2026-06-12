---
title: "apparmor trouble"
date: 2010-06-24
forum: Security
---

### Post by jdunn on 2010-06-24
I followed [this]("http://ubuntuforums.org/showthread.php?t=1008906") apparmor howto and can't get past a basic stub file. 'sudo genprof <app>' creates the stub and then prompts me to run the app but when I scan, non of the log entries are added to the profile leaving me with a useless stub profile. Tried this for firefox and google-chrome.  please help.

---

### Post by jdunn on 2010-06-24
bump

---

### Post by cariboo on 2010-06-25
Please don't bump until 24 hours has elapsed.

---

### Post by bodhi.zazen on 2010-06-25
Firefox has an apparmor profile in the repository, I suggest you start with that.

For chrome, I have a chromium profile here :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

In general, genprof is extreemely generic and you write profile by running your new profile in complain mode, watching the logs, and manually adding rules.

The tools to manage profiles for you, as you can see, do not work well.

Browsers are not the best place to start. Everyone uses browsers very different and browsers need extensive access. For example, browsers need access to networking, X, do you open documents with your browser -> now you need to allow Open Office , do you open links from other apps with your browser ? How about watch videos ? Open other external apps ? Download ? Java ? 

you get the idea.

learn to write a profile on a smaller application, then try a browser.

---

### Post by jdunn on 2010-06-26
bodhi,
Thanks.  I made slight changes to your Chromium code to use with Chrome.  Basically, I replaced Chromium path info with Chromes but I have these modified lines:

```
owner @{HOME}/{Desktop,Downloads}/ rw,
  owner @{HOME}/{Desktop,Downloads}/** rw,
```

My assumption is this should allow Chrome to save downloaded files to Desktop or Downloads and not Documents.  However, I tested it out and I can still save downloads in the Documents folder and other locations not in the rules list.

---

### Post by bodhi.zazen on 2010-06-26
> **jdunn said:**
> bodhi,
Thanks.  I made slight changes to your Chromium code to use with Chrome.  Basically, I replaced Chromium path info with Chromes but I have these modified lines:

```
owner @{HOME}/{Desktop,Downloads}/ rw,
  owner @{HOME}/{Desktop,Downloads}/** rw,
```My assumption is this should allow Chrome to save downloaded files to Desktop or Downloads and not Documents.  However, I tested it out and I can still save downloads in the Documents folder and other locations not in the rules list.

Sweet, looks as if it is coming along nicely.

Remember to re-load the profile after you have made changes.

If you are having problems, post the profile and I will look it over.

---

