---
title: "Are Google and Mozilla waiting for a baby?"
date: 2006-11-24
forum: The Cafe
---

### Post by ago on 2006-11-24
We all know the two are having an affair, but might the story "evolve"? The integration of Mozilla and Google may go well beyond the use of Google as default search engine... And in case you are wondering, yes, I am talking about Google "OS"... 

Let's have a look at the parent genes. On the the desktop side, we have... ...Mozilla: 

[list]XPCOM/XULRunner 
[*] A local web-server (doubling up as application server providing XUL)
[*] A web-framework (something like RoR but fine-tuned for XUL and better integrated with XPCOM)
[*] A side-bar similar to google-desktop used as task-oriented panel + taskbar + notification + systray (ever wondered why google called their side-bar: google-DESKTOP?)
[*] Firefox
[*] Flash player (manage a trois?)[/list]

On the server side, running from Google HQ:

[list][*] A remote web-server (doubling up as application server providing XUL)
[*] A remote "hard-disk"[/list]

Put the two (or three) together and you have quite a nice combination. Let me explain.

This is not strictly an OS but more like an application framework that can run on any platform where Firefox (3) runs. It can easily be turned into a full OS by bundling it with Linux/BSD, but that is another story... Applications are essentially XUL files running locally, and they are provided by the local web-server and/or the remote web-server (and cached locally). They can optionally embed flash/html/svg components. Data (docs, emails, bookmarks) is stored on the remote hard-disk and is downloaded and synced locally so that it can be used offline. All data can optionally be shared. 

Why is this baby so special?

[list][*] Native speed, but with web-OS flexibility. Like an OS on USB-key, but without the USB-Key.
[*] Cross platform
[*] It can be downloaded and it should weight about 20-30 MB
[*] One click installation
[*] It can run on top of an existing OS (no partitioning)
[*] It can replace a desktop environoment or coexist with it, managing its own applications
[*] It can be bundled with Linux and a window manager (even Beryl ) to create a full blown OS, with a fairly small footprint
[*] All Mozilla apps are supported by default
[*] Seamless integration of local/remote apps, local/remote data, traditional GUI/web GUI.
[*] Not all the functionality of an application needs to be installed/downloaded beforehand, so applications can be downloaded on-the-fly depending on user interaction
[*] But it should still be possible to install an application in a more traditional way in order to accomodate for offline workflow.[/list]

Even if Google is not interested, it might be a nice FOSS project, possibly using a distributed web-server and a "remote hard-disk" based on a p2p grid... In fact it might be a nice FOSS project even if Google is interested, to give the same flexibility to those that have privacy concerns... 

[http://agolb.blogspot.com/2006/11/are-google-and-mozilla-waiting-for.html](http://agolb.blogspot.com/2006/11/are-google-and-mozilla-waiting-for.html)

---

### Post by ago on 2006-11-24
IF such Google"OS" had to materialize, what would be the fate of Ubuntu? 

It is probably good news for Linux, since this "OS" might be bundled to a light OS/WM to provide a full blown stand-alone OS. And Linux is quite clearly a good candidate together with BSD. This will probably come in a later stage, after the "OS" becomes accepted ("that is all you use now? so why pay for windows/mac? get a free GooglePC"). It is also good news for Firefox. But for Ubuntu?

As mentioned, it should be possible to run such an "OS" on top of a traditional OS/desktop, like Ubuntu. So in a first stage it would simply provide some more applications. 

But, as applications are ported or rewritten to/for the XUL platform, there would be little point in using standard apps, only usable locally. Also the delivery mechanism of packages would be different, since the apps would be provided on-the-fly by the remote web/app server. This implies that apt will become mostly redundant for desktop use. Will that (or a FOSS implementation of it) be able to take over Ubuntu in the coming years?

---

### Post by Kernel Sanders on 2006-11-24
I for one would love a google OS :cool: 

Google is my master now :cool:

---

