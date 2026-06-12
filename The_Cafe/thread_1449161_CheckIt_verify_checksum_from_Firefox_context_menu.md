---
title: "CheckIt: verify checksum from Firefox context menu"
date: 2010-04-07
forum: The Cafe
---

### Post by lovinglinux on 2010-04-07
I have developed a new extension for Firefox that allows compare a file checksum with the checksum posted on the download site. 

The extension is pretty simple, but very useful for me. You can simply select the hash number displayed on a site, then select the algorithm and pick a file to compare. The extension will compare the checksum selected from the site with the one generated from the file and produce a positive message or an negative alert.

It supports MD2, MD5, SHA-1, SHA-256, SHA-384 and SHA-512 algorithms.

[IMG]http://lh6.ggpht.com/_EPRFmO0pKhs/TGalVU_eSAI/AAAAAAAAA7o/x_U5F5V2CL8/s800/checkit-screenshot-001.jpg[/IMG]

[**Download, Video Demo & Instructions](http://www.webgapps.org/addons/checkit)**

Any comments and suggestions will be much appreciated. I hope you like it.

---

### Post by dearingj on 2010-04-07
Looks useful; I'm downloading it now.

---

### Post by lovinglinux on 2010-04-07
> **dearingj said:**
> Looks useful; I'm downloading it now.

Thanks. Well, I am a suspect, but is really useful for me. I thought about this add-on while I was preparing to download and install Lucid Linx yesterday. I postponed the installation of the OS and created the extension. So here it is.

---

### Post by undecim on 2010-04-07
Very nice. I'm installing it now!

I have the Web Developer plugin as well, so I'll let you know if I have any issues with it.

EDIT: Update:

I installed it and it works like a charm! This will save me a lot of time!

Only problem I see is that it doesn't trim whitespace from the selected area. I tried one hash with and the same one without the trailing tab, but it tells me they mismatch (even though the error dialog shows the exact same hashes, lol).

Another feature that would be great is if the addon would recognize hashes on the page and let you just right-click instead of highlighting (this might even workaround the Web Dev comparability issue... idk)

Again, it's great piece of code, and I thank you for it!

---

### Post by lovinglinux on 2010-04-07
> **undecim said:**
> Only problem I see is that it doesn't trim whitespace from the selected area. I tried one hash with and the same one without the trailing tab, but it tells me they mismatch (even though the error dialog shows the exact same hashes, lol).

This should be easily fixable. Could you please provide a link to the hash so I can test it.

> **undecim said:**
> Another feature that would be great is if the addon would recognize hashes on the page and let you just right-click instead of highlighting (this might even workaround the Web Dev comparability issue... idk)

What I do is double click over the hash and Firefox selects the entire string. Nevertheless, I guess I could implement that feature. I will look into it. 

> **undecim said:**
> Again, it's great piece of code, and I thank you for it!

You are welcome. Thanks for the suggestion and bug report.

---

### Post by undecim on 2010-04-07
> **lovinglinux said:**
> This should be easily fixable. Could you please provide a link to the hash so I can test it.

at 

[http://www.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/2009.08/sha1sums.txt](http://www.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/2009.08/sha1sums.txt)

the hash for archlinux-2009.08-core-x86_64.img

I selected the hash and the space (tab) between the hash and file name, which causes a false negative.

[ATTACH]152616[/ATTACH]

Selecting only the hash (or doubleclicking, like you mentioned) works fine though.

---

### Post by lovinglinux on 2010-04-07
> **undecim said:**
> at 

[http://www.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/2009.08/sha1sums.txt](http://www.gtlib.gatech.edu/pub/linux/distributions/archlinux/iso/2009.08/sha1sums.txt)

the hash for archlinux-2009.08-core-x86_64.img

I selected the hash and the space (tab) between the hash and file name, which causes a false negative.

[ATTACH]152616[/ATTACH]

Selecting only the hash (or doubleclicking, like you mentioned) works fine though.

EDIT: 

:oops: the fix is not working as I thought it was. I will fix this for next version.

---

### Post by lovinglinux on 2010-04-07
I did something really stupid on the allegedly fixed version, but I won't tell :)

---

### Post by Hero of the Day on 2010-04-07
awesome!

---

### Post by lovinglinux on 2010-04-15
CheckIt has been approved by Mozilla, so now you can get updates automatically, through Firefox Add-ons manager. Please install the latest versio to make sure you will get future updates.

---

### Post by lovinglinux on 2010-04-29
Lucid Lynx is about to be released, so I though would be interesting to bump this thread.

---

### Post by Shakz on 2010-04-29
> **lovinglinux said:**
> Lucid Lynx is about to be released, so I though would be interesting to bump this thread.

good call!

---

### Post by lovinglinux on 2010-04-29
> **Shakz said:**
> good call!

Thanks. I hope you like it.

---

### Post by Dupoint on 2010-04-29
This is going to make verifying my .iso downloads at lot easyer. Thank you sir.

---

### Post by lovinglinux on 2010-04-29
> **Dupoint said:**
> This is going to make verifying my .iso downloads at lot easyer. Thank you sir.

You are welcome.

---

### Post by lovinglinux on 2010-05-07
I have released version 1.0.2, which fixes previous compatibility issues, that could result in false negatives.

[Download](http://checkit-extension.blogspot.com/)

---

### Post by lovinglinux on 2010-07-21
CheckIt version 1.0.4 has been released today and is available for download through the extension site Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors. It is also available through the Beta channel as 1.0.4rc, but it is identical to the final version.

This version adds compatibility with Firefox 4.0b3pre.

---

### Post by 101011010010 on 2010-07-21
Thank you for all your hard work.

---

### Post by lovinglinux on 2010-07-21
> **101011010010 said:**
> Thank you for all your hard work.

You are welcome.

---

### Post by lovinglinux on 2010-07-25
CheckIt version 1.0.6 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version fixes an issue with hash spaces and upper case letters.

---

### Post by lovinglinux on 2010-07-25
There were some issues with versions 1.0.5 and 1.0.6, so they were removed form the site.

Current download is 1.0.4.

---

### Post by lovinglinux on 2010-07-26
CheckIt version 1.0.8 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version fixed an issue with upper case hashes and spaces.

---

### Post by aboettger on 2010-09-16
Doesn't works in Firefox 4.0b7pre.
I have an empty menu (except "Preferences"). All options are checked.

---

### Post by lovinglinux on 2010-09-16
> **aboettger said:**
> Doesn't works in Firefox 4.0b7pre.
I have an empty menu (except "Preferences"). All options are checked.

It works. You need to highlight a hash number in a web site to see the options in the context menu. Once you highlight the hash text, go to the context menu and select the desired algorithm, then it will prompt for the file to compare.

---

### Post by lovinglinux on 2011-04-08
CheckIt version 1.1.2 has been released today and is available for download.

Due to requests, the selected hash menu has been moved back to the context menu.The toolbar menu still contains the options to compare files, which has been enhanced. Now is possible to generate hash for a single file, compare a file with clipboard content and compare a file with the content of a txt hash file.

Changelog

[LIST]
[*]moved selected hash test menu back to context
[*]added option to compare file with clipboard content
[*]added option to compare file with hash file
[*]added option to generate hash for a single file
[*]added compatibility with Firefox 4.2a1pre
[*]reduced alert icon size
[*]fixed menu bug
[/LIST]

---

### Post by beew on 2011-04-08
Nice job, will use it as soon as there is a chance. You rock!

---

### Post by lovinglinux on 2011-04-08
> **beew said:**
> Nice job, will use it as soon as there is a chance. You rock!

Thanks.

---

### Post by lovinglinux on 2011-04-15
CheckIt version 1.1.3 has been released today and is available for download.

This version fixes some bugs related to uppercase validation and alerts.

**Changelog**

[LIST]
[*]fixed upper case issues
[*]fixed alerts localization
[/LIST]

---

