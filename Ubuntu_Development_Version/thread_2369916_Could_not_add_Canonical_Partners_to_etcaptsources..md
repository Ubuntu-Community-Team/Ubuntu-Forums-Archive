---
title: "Could not add Canonical Partners to /etc/apt/sources.list"
date: 2017-08-28
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2017-08-28
Don't know how important this is at this stage but, I like to have all of my options open.

I tried to enable Canonical Partners via Software and Updates and it just hung there not doing anything.

Then I tried to open /etc/apt/sources.list via gedit and it gave an error.

So I entered **gksudo gedit /etc/apt/sources.list** and that allowed me to remove the # and have Canonical Partners as a source.

There is currently nothing there but, at least I will have it there when it does something.

---

### Post by harry332 on 2017-08-28
Does not hang here with synaptic.
And these can be found there:
adobe-flashplugin
google-cloud-sdk

---

### Post by Cavsfan on 2017-08-29
> **harry332 said:**
> Does not hang here with synaptic.
And these can be found there:
adobe-flashplugin
google-cloud-sdk

Thanks but, when I tried to install **adobe-flashplugin**, it was going to remove **flashplugin-installer**.
Doesn't **flashplugin-installer** suffice for flash? I don't really use google cloud or any cloud for that matter.

I did notice it suggested some fonts I don't currently have like msttcorefonts, ttf-dejavu, etc.

On a side note, not related, sometimes my cursor disappears while typing in the forum. It is there but, I have to guess where it is.
If I alt+tab to terminal or whatever and come back it re-appears. Guess that's just the alpha maybe.

---

### Post by harry332 on 2017-08-30
That is correct.
In order to install the Adobe Flash you need to install either adobe-flashplugin or flashplugin-installer.
You do not need nor you cannot have both.

---

### Post by Cavsfan on 2017-08-30
> **harry332 said:**
> In order to install the Adobe Flash you need to install either adobe-flashplugin or flashplugin-installer.
[COLOR=#000000]You do not need nor you cannot have both.[/COLOR]

I guess that was intended to be a question: do I need need adobe-flashplugin if I already have flashplugin-installer?
Also is one better than the other?

---

### Post by deadflowr on 2017-08-30
> **Cavsfan said:**
> I guess that was intended to be a question: do I need need adobe-flashplugin if I already have flashplugin-installer?
Also is one better than the other?

I believe you only need adobe-flashplugin if you require the pepperflash version.
If you use chromium or some chromium-based browser (excluding google-chrome, of course) then you would need it.
(opera, vivaldi come to mind as chromium based)

If you do not use one of those, then no need for the adobe-flashplugin, as flashplugin-installer will install the regular version used by Firefox. 
(and whatever applications utiliize flash)

Last I remember, the flashplugin-installer came with just the npapi version and the adobe-flashplugin version came with both the npapi and ppapi versions.

---

### Post by #&amp;thj^% on 2017-08-30
> **harry332 said:**
> That is correct.
In order to install the Adobe Flash you need to install either adobe-flashplugin or flashplugin-installer.
You do not need nor you cannot have both.

Just depends on usage: Here for example:
```
flashplugin
Name            : flashplugin
Version         : 26.0.0.151-1
Description     : Adobe Flash Player NPAPI
Architecture    : x86_64
URL             : https://get.adobe.com/flashplayer/
Licenses        : custom  LGPL
Groups          : None
Provides        : None
Depends On      : libxt  gtk2  nss  curl  hicolor-icon-theme
Optional Deps   : libvdpau: GPU acceleration on Nvidia cards [installed]
Required By     : None
Optional For    : pepper-flash
Conflicts With  : None
Replaces        : None
Installed Size  : 19.06 MiB
Packager        : Evangelos Foutras <evangelos@foutrelis.com>
Build Date      : Tue 08 Aug 2017 11:07:49 AM MDT
Install Date    : Wed 09 Aug 2017 07:00:04 AM MDT
Install Reason  : Explicitly installed
Install Script  : No
Validated By    : Signature
## And
pepper-flash
Name            : pepper-flash
Version         : 26.0.0.151-1
Description     : Adobe Flash Player PPAPI
Architecture    : x86_64
URL             : https://get.adobe.com/flashplayer/
Licenses        : custom  LGPL
Groups          : None
Provides        : None
Depends On      : gcc-libs
Optional Deps   : flashplugin: settings utility [installed]
Required By     : None
Optional For    : brave  chromium
Conflicts With  : None
Replaces        : None
Installed Size  : 20.55 MiB
Packager        : Evangelos Foutras <evangelos@foutrelis.com>
Build Date      : Tue 08 Aug 2017 11:07:56 AM MDT
Install Date    : Wed 09 Aug 2017 07:00:06 AM MDT
Install Reason  : Explicitly installed
Install Script  : No
Validated By    : Signature

```
As you can tell I use both. " Adobe Flash Player PPAPI"  "Adobe Flash Player NPAPI"

---

### Post by Cavsfan on 2017-08-31
OK, thanks! I opted to install adobe-flashplugin and some MS fonts.

I use Vivaldi exclusively because it seems faster than any other browser and plus it has as an extension my VPN.
I use it on all 3 currently installed Ubuntu versions, Arch Linux and even Windows 10.
Although I believe flash ran OK before, I'm good with adobe-flash. It is set to detect and allow important flash content only.

Otherwise I think I have to right click on it to run any other flash.

Edit: 1fallen, that's on Arch isn't it ;)
I know of no way to get that display on Ubuntu.

---

