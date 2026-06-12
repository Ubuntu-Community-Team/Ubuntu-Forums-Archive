---
title: "VMWare Configuration File - Where do i find it?"
date: 2012-04-08
forum: Virtualisation
---

### Post by mixim on 2012-04-08
Hello Guys,

When im trying to enter my license key the last step is to register the product. When i do this, i get following error message (screen also attached):

```
VMware Workstation could not find a suitable default 
browser and is therefore unable to provide the information 
you requested. Please install FireFox, Mozilla or Netscape. 
If you wish to use a different web browser, please place 
the following in your ~/.vmware/preferences file:

pref.webBrowser = "/path/to/browser"
```

I am using Chromium and would like to edit this setting in the preferences file. I know it directs me to a path, but i somehow can't reach it, neither by bash or the GUI filemanager.

How can i edit this?

Would be grateful for any input... Regards Joakim from Sweden

---

### Post by dcstar on 2012-04-09
> **mixim said:**
> Hello Guys,

When im trying to enter my license key the last step is to register the product. When i do this, i get following error message (screen also attached):

```
VMware Workstation could not find a suitable default 
browser and is therefore unable to provide the information 
you requested. Please install FireFox, Mozilla or Netscape. 
If you wish to use a different web browser, please place 
the following in your ~/.vmware/preferences file:

pref.webBrowser = "/path/to/browser"
```

I am using Chromium and would like to edit this setting in the preferences file. I know it directs me to a path, but i somehow can't reach it, neither by bash or the GUI filemanager.

How can i edit this?


```
gedit ~/.vmware/preferences
```

---

### Post by mixim on 2012-04-09
> **dcstar said:**
> ```
gedit ~/.vmware/preferences
```

I did try that before, i. But all it does is open an empty file. Seems that VMWare never created any preferences file.

This confused me in the beginning, but i realized that maybe there is simply no configuration file created by default. 

So for other novices, i did this (im using leafpad instead of gedit):

```
sudo leafpad ~/.vmware/preferences
```

added this line (im using chromium):

```
pref.webBrowser = "/usr/bin/chromium-browser"
```

Saved, and it worked.

Thanks for the feedback, u confirmed that I was on the right path =)

---

### Post by dcstar on 2012-04-10
> **mixim said:**
> 
...........
Saved, and it worked.


Then **mark** the thread.

---

