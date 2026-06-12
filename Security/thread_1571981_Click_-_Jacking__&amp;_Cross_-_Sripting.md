---
title: "Click - Jacking  &amp; Cross - Sripting"
date: 2010-09-10
forum: Security
---

### Post by Frogs Hair on 2010-09-10
In the past month I have received a click - jack and cross scripting warning while visiting OMG Ubuntu . Could I be being redirected to a fake mirror site or should this site be avoided ? I am using Namoroka with Adblock , No script , and better privacy. This site has some good information , I'm just wondering whats up. [http://en.wikipedia.org/wiki/Cross-site_scripting](http://en.wikipedia.org/wiki/Cross-site_scripting)

---

### Post by OpSecShellshock on 2010-09-10
Not sure. I visit the site frequently and never see such warnings. They do have a lot of little social widgets embedded on the page. If they're also being run from sites you've already allowed, I could see where that sort of warning could come up. Without more context it would be hard to say. For example, did the warning come from Firefox itself, or did it come from NoScript?

I ask because NoScript should have protection for both clickjacking and XSS on any site that's not on the whitelist. I should note that when I visit the site, I do not have scripts enabled (as they don't seem necessary in order to read the posts).

I just looked up omgubuntu.co.uk on XSSed, and it's not listed. That doesn't really mean anything other than that it wasn't reported, but they're usually one of the go-to places for people who discover stuff (as well as for people looking for easy targets).

---

### Post by Frogs Hair on 2010-09-10
The warnings came from Firefox and I am not a member of OMG Ubuntu . The click-jacking warning came when I was highlighting some ppa instructions to copy. The script warning came during a random visit and rarely visit the site, I use Web Ud8 most of the time.

---

### Post by OpSecShellshock on 2010-09-11
> **Frogs Hair said:**
> The warnings came from Firefox and I am not a member of OMG Ubuntu . The click-jacking warning came when I was highlighting some ppa instructions to copy. The script warning came during a random visit and rarely visit the site, I use Web Ud8 most of the time.

Not sure then, sorry. I suspect it might be local. Maybe a Greasemonkey script?

---

