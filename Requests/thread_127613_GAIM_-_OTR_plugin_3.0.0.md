---
title: "GAIM - OTR plugin 3.0.0"
date: 2006-02-09
forum: Requests
---

### Post by JGJones on 2006-02-09
[http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)

There is now a Gaim-otr 3.0.0 with support for OTR protocol version 2 (which I believe GoogleTalk on Windows use?)

Currently we have Gaim-otr 2.0.2.

I don't know if Dapper Drake have 3.0.0 but if so, can we have this backported? As far as I can see, it doesn't require any dependancies.

Many thanks.

JGJones

---

### Post by dweez on 2006-06-19
Following the instructions on [http://www.cypherpunks.ca/otr/ubuntu-install/otr-setup.html](http://www.cypherpunks.ca/otr/ubuntu-install/otr-setup.html) doesn't work for me.  I get the following error when I click on Plugin Details for the OTR plugin.
> Error: ABI version mismatch 1.0.x (need 2.0.x).  Check the plugin website for an update.

Anyone know how to resolve this?

---

### Post by jrbonewitz on 2006-07-02
Yeah, I get the same error mesg. 

I would also like to know how to solve this.

---

### Post by dweez on 2006-07-12
bump

---

### Post by methane on 2006-07-27
I get this same error.  ABI mismatch.  I'm interested in a solution too since I can't seem to get gaim-otr version 2.0.2 to download via apt-get.

---

### Post by dweez on 2006-07-28
*bump*

Anyone?

---

### Post by colklink on 2006-09-01
I'm still having this issue. Does anyone have a fix?

---

### Post by colklink on 2006-09-01
ok, here's how I got OTR installed. I decided to compile it from source.

Go to [http://www.cypherpunks.ca/otr/#downloads](http://www.cypherpunks.ca/otr/#downloads) and grab the source for both libotr and OTR. Also, I grabbed the patch for gaim beta 2 (even though current is beta 3). 

Compile and install libotr.
Copy the patch file into the OTR source directory.
Patch OTR with the beta 2 patch:
```
patch -p0 < gaim2b2-otr.dff
```

Do your typical "./configure && make && sudo make install" goodness.

Now, this was all obvious, but what was happening to me was that I was getting a make error about missing header files (*.h files). Apparently, the Debian package manager is installing gaim's headers to /usr/include/gaim, but OTR's source was looking for them in /usr/local/include/gaim. So, while it probably isn't the best solution and might cause some problems later with gaim, I just copied the libraries over to /usr/local/include/gaim. This got rid of the make errors. However, this will install OTR to /usr/local/lib/gaim and gaim will not see the plugin. So, you need to copy the OTR files from /usr/local/lib/gaim to /usr/lib/gaim. Now OTR works just fine.

If anyone has some better suggestions on how to fix this better, please let me know. I have a feeling there was a much easier and better way, but thought I would share anyway.

---

### Post by xyverz on 2006-09-19
I'm unable to build libotr because I keep getting sanity check errors for c++ preprocessor.  I've installed gcc and cpp versions 2.95, 3.3, and 4.0 and I keep getting this error.  I'm running dapper kubuntu.  I'd really like to get this working, but nothing's helping.  Any suggestions would be greatly appreciated.

---

### Post by xyverz on 2006-09-19
Nevermind, found the following post:

[http://www.ubuntuforums.org/showthread.php?t=122893](http://www.ubuntuforums.org/showthread.php?t=122893)

and installed build-essentials.  The building process is working now. :-)

---

### Post by dbrum on 2006-09-26
I did:

downloaded libotr and otr sources.

built and installed libotr.
patched otr with .diff file from otr site
building/install on otr: generates:

checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 gaim >= 1.0... configure: error: glib
./configure: line 19502: exit: gtk: numeric argument required
./configure: line 19502: exit: gtk: numeric argument required

Not sure now how to proceeed...getting GAIM 2.0 b3 and OTR is proving harder then pulling teeth.

---

### Post by chewie124 on 2006-10-24
Anybody have any luck in resolving this issue?  I run into the exact same problem.

---

### Post by shizow on 2006-10-25
anyone got beta4 and otr working?

---

### Post by dweez on 2006-10-25
Actually, I updated my system to the Edgy Eft dev build just to try it out and decided to see if I still had the issue with GAIM/ORT.  Oddly enough, now the OTR plugin works perfectly.

Probably not the solution you wanted, but it's what I did.

---

### Post by loko on 2006-11-12
i also run intro trouble building otr for gaim.

i installed libotr, then i patched gaim-otr with the diff.

but i get an error during compiling gaim-otr:

```
gtk-dialog.c:33:22: error: gtkstock.h: No such file or directory
gtk-dialog.c: In function 'create_dialog':
gtk-dialog.c:651: error: 'GAIM_STOCK_DIALOG_ERROR' undeclared (first use in this function)
gtk-dialog.c:651: error: (Each undeclared identifier is reported only once
gtk-dialog.c:651: error: for each function it appears in.)
gtk-dialog.c:655: error: 'GAIM_STOCK_DIALOG_WARNING' undeclared (first use in this function)
gtk-dialog.c:659: error: 'GAIM_STOCK_DIALOG_INFO' undeclared (first use in this function)
make[1]: *** [gtk-dialog.lo] Fehler 1
```

i can see that this error means that i have no gtkstock.h, but i have libgtk2-dev installed and gtkstock is there.

if i take a look in the package-list, gaim-dev also provides gtkstock.h, but i installed gaim 2.0+beta5 and i could not found a gtkstock.h-file provided with gaim.

but i do not know if this is the real problem, can somebody help?

---

### Post by loko on 2006-11-12
i found the solution.

in gaim beta5 maybe also in beta4, gtkstock.h changed its name to gaimstock.h.

the only thing to do is to change gtkstock.h to gaimstock.h in the patch (gaim2b2-otr.diff)

and then patch it against gaim-otr

---

### Post by j-strap2 on 2006-12-02
Nice one loko. I edited the patch as you said and the plugin compiled fine. I had to move the compiled OTR plugin from /usr/lib/gaim to /usr/local/lib/gaim to get the plugin to show up in Gaim.

---

### Post by threespacemen on 2007-01-22
> **dbrum said:**
> checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 gaim >= 1.0... configure: error: glib
./configure: line 19502: exit: gtk: numeric argument required
./configure: line 19502: exit: gtk: numeric argument required

Not sure now how to proceeed...getting GAIM 2.0 b3 and OTR is proving harder then pulling teeth.

Still having problems with this one?

I came across the same thing, and figured out I needed to install libgtk2.0-dev. You might also need gaim-dev, but I'm not 100% sure.

```

$ sudo apt-get install gaim-dev
$ sudo apt-get install libgtk2.0-dev

```

Now I have the successfully compiled gaim-otr.la and gaim-otr.so sitting in both /usr/local/lib/gaim and /usr/lib/gaim (copied from the former to the latter), yet the plugin doesn't appear in gaim at all... Using gaim 2.0.0beta6 from repository.debuntu.org - anyone got any ideas?

---

