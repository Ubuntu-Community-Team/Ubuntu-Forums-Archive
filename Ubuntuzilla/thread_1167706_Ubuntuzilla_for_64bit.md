---
title: "Ubuntuzilla for 64bit"
date: 2009-05-23
forum: Ubuntuzilla
---

### Post by afrodeity on 2009-05-23
Getting this to run on 64bit, instructions please. Also, one question: Is there an option to roll-back changes? Can one install the latest Firefox and keep an old Seamonkey? Is there a graphical menu, or will all of this be so automated, my Thunderbird will fly out the window?

---

### Post by nanotube on 2009-05-23
Hi
unless something changed in jaunty, all you need to do is install the latest amd64 .deb of ubuntuzilla, which will pull in all the 64bit compatibility libraries required to run the official mozilla build (which is a 32 bit build).

also, if you read the ubuntuzilla website, you'll see that yes, there's an uninstall function that you can use, and that the installs are separate and independent for firefox, seamonkey, and thunderbird (so you can choose exactly which ones you want).

there's no graphical menu, run the specified commands from the terminal, once you install ubuntuzilla. (see website for instructions).

---

### Post by afrodeity on 2009-05-24
thanks for clearing that up.

---

### Post by beartham on 2009-05-28
Hi,

I just used Ubuntuzilla AMD64 to install Firefox. But Firefox can't raise any website. Not even the firstrun site. I can raise my router (192.168.1.1) ok. But nothing outside that. I am using Konqueror for this post. So my Internet is ok. Any thoughts about what may be wrong. :?:

I forgot: This is a new installation of Kubuntu 9.04 Jaunty Jackalope. My Xubuntu 8.04 is a remote VPS. No prior Firefox on this box.

---

### Post by beartham on 2009-05-28
Follow up:

I looked at the Firefox error console. Here are first two messages:

```
Failed to load XPCOM component: /opt/firefox/components/libnkgnomevfs.so
```
```
Failed to load XPCOM component: /opt/firefox/components/libmozgnome.so
```

Then this javascript error message:

```
Error: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIChannel.contentType]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "JS frame :: file:///opt/firefox/components/FeedProcessor.js :: FP_onStartRequest :: line 1440"  data: no]
Source File: file:///opt/firefox/components/FeedProcessor.js
Line: 1440
```

Here is the Js function where the error occurred:

  ```
// The XMLReader will throw sensible exceptions if these get called
  // out of order.
  onStartRequest: function FP_onStartRequest(request, context) {
    // this will throw if the request is not a channel, but so will nsParser.
    var channel = request.QueryInterface(Ci.nsIChannel);
    channel.contentType = "application/vnd.mozilla.maybe.feed";
    this._reader.onStartRequest(request, context);
```

Its last line is line 1441.

Does this mean that the missing XPCOM component is the cause? Both the 
shared object libraries do exist. But I couldn't list their contents.

I also used Ubuntuzilla to download and install Seamonkey. It also can't access any website, but does access the router, just like Firefox. I could not get it to print any details about the error, however. I assume it is the same problem.

Any ideas?

---

### Post by nanotube on 2009-05-28
and the ubuntu repo version of firefox has no similar problem? have you checked?

you can try running from terminal "firefox.ubuntu" to run the repos version (that's where ubuntuzilla sticks it by default).

exit any running instances of firefox before starting firefox.ubuntu. otherwise it will detect running firefox, and simply spawn a new window of existing process, which is not what we want.

p.s. i'll be away for a couple of days, so will reply when i check back then. in the meantime, please post any further findings.

---

### Post by beartham on 2009-05-29
I was able to get firefox.ubuntu to work as follows:

```
export LD_LIBRARY_PATH=/usr/lib32
firefox.ubuntu
```

So I created a /usr/bin/firefox shell script with this content, and renamed the previous firefox symlink to firefox_opt (firefox_opt -> /opt/firefox/firefox)

When I execute it, as follows:

```
bear@pavilion64:~$ firefox_opt
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(firefox-bin:17361): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(firefox-bin:17361): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

```

the Firefox window comes up, but it can't access any website, even with LD_LIBRARY_PATH set to /usr/lib32.

The same problem still exists with seamonkey also:

```
bear@pavilion64:~$ echo $LD_LIBRARY_PATH
/usr/lib32
bear@pavilion64:~$ seamonkey
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

(seamonkey-bin:17252): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64
bear@pavilion64:~$

```

The SeaMonkey window comes up, but can't access any websites.

I presume the problem is the inability to access XPCOM from the libmozgnome.so or libnkgnomevfs.so libs, as before.

Yesterday I tried listing these so libs using nm:

```
bear@pavilion64:/opt/firefox/components$ nm libmozgnome.so
nm: libmozgnome.so: no symbols
bear@pavilion64:/opt/firefox/components$ nm libnkgnomevfs.so
nm: libnkgnomevfs.so: no symbols
bear@pavilion64:/opt/firefox/components$ nm -n libnkgnomevfs.so
nm: libnkgnomevfs.so: no symbols
bear@pavilion64:/opt/firefox/components$

```

If nm is the right utility to list such libs, then it is strange that no symbols were found? Could this be a clue that the AMD64 version of the Ubuntuzilla script is not correctly referencing the so libs, or that the libs are corrupted. I understand that it is installing 32-bit versions of Firefox and Seamonkey. 

I presume that the dynamic-linking so libs must be referenced using names.

I don't know how to fix the GTK messages from within the Firefox or SeaMonkey binaries to reference /usr/lib32 instead of /usr/lib (which is 64-bit libraries on this machine). I can't believe these references are hard coded in the executables.

regards, beartham

---

### Post by shoeheight on 2009-05-30
I have the exact same error messages and same problem on a new 9.04 install.

I'm looking forward to hearing the fix to this!

Thanks

PS - maybe this should be a new post with a more useful title..

---

### Post by shoeheight on 2009-05-30
As it turns out there is already a posting on this...

[http://ubuntuforums.org/showthread.php?p=7371371#post7371371](http://ubuntuforums.org/showthread.php?p=7371371#post7371371)

It fixed it for me, I hope it does the same for you.  IPv6 was the problem.  Must be a 64bit bug.

---

### Post by beartham on 2009-05-30
This did fix it for me, and with SeaMonkey too.:p

Thanks shoeheight for your specific instructions regarding *about:config*. That was new to me.

---

