---
title: "Request: gkrellm 2.2.6 or 2.2.7"
date: 2005-07-02
forum: Ubuntu Backports
---

### Post by whitecastle456 on 2005-07-02
Changelogs:
> 2.2.7 - Tue May 24, 2005
------------------------
	* gkrellmd can send a network interface connect time to be displayed
	  on client timer button panels by configuring a net-timer in gkrellmd.conf.
	* Don't add virtual disk (/dev/mdX) stats to composite disk.
	* Bugfixes:
	  o server/main.c inet6 compile error on machines with old libc.
	  o Philipp Hartmann patch: add gnutls multithread initialization to mail.c
	  o While mixing draw_decal_text and decal_scroll_text calls on transparent
	    panels the text layer pixmap was not cleanup up properly.
	* Translation updates
	  o de.po

2.2.6 - Fri May 13, 2005
------------------------
	* Samuel Mimram patch: preferentially link to gnutls over openssl to avoid
	  GPL license compatibility issue.
	* Stanislav Likavcan patch: add monitoring of ibm acpi sensors to linux.c.
	* UI improvement in fs.c and mail.c config button sensitivities and labels.
	* Bugfixes:
	  o Test for not force creating user mailbox did not consider a configured
	    mail fetch.
	  o gkrellmd server mail check was missing the gkrellmd_need_serve() call
	    and server/mail.c mailbox code needed syncing with src/mail.c.
	  o gkrellmd glib 1.2 g_file_test compatibility was broken.
	  o gkrellmd debug-level option was missing.
	  o Darwin Makefile: add HAVE_GETADDRINFO=1
	  o Don Bostrom patch: when remote mail checking, handle select() EINTR.
	  o Charles Bailey patches:
	    1) darwin.c and Makefile tweaks for building on OS X 10.3.8.
	    2) darwin.c prevent left bit sign extension when shifting memory
	       monitor data.
	  o Don't read disabled sensors in the sensors thread.
	* Translation updates
	  o fr.po from Jerome UZEL
	  o it.po from Massimo Maiurana
	  o ja.po from Takeshi AIHANA 

I'd really like this for the IBM-ACPI support (I'm on a thinkpad).

Thanks,
Joe

---

### Post by Slo Mo Snail on 2005-07-04
Currently not in breezy... will package it when it's there

---

### Post by ghostintheshell on 2005-07-13
Hi,

I so wanted too the latest gkrellm!
Then I tried to install it from source and it worked :)

How to (this is the way I did it):

- Install gkrellm 2.2.4 from synaptic (should be already done ;))
- Quit gkrellm
- Uninstall all gkrellm related packages (from synaptic packages manager, it's easy)

- Download the latest sources file [here](http://members.dslextreme.com/users/billw/gkrellm/gkrellm-2.2.7.tar.bz2) (from the gkrellm web site)

- Un-tar the file
- Move the new folder to /usr/local/src (sudo)
- Go to /usr/local/src/gkrellm-2.2.7/ in the terminal
- Type "make" (any error message displayed in my case!)
- Type "sudo make install INSTALLROOT=/usr" 

- Finally, type "gkrellm &" in a terminal to launch gkrellm 2.2.7

That's all  ;-) 

I don't know if it will do the trick for you but that did it for me!

Personnaly, I wanted a version > 2.2.4 for the latest ethernet statistics module (with month per month informations and not only the currently month) and it's now ok :)

-- sorry for my crappy english, not so easy to compile ;)

---

### Post by Slo Mo Snail on 2005-07-15
it won't be updated for breezy so there will be no backport of 2.2.7 until breezy is released... sorry :(

---

### Post by ghostintheshell on 2005-07-16
[QUOTE=Slo Mo Snail]it won't be updated for breezy so there will be no backport of 2.2.7 until breezy is released... sorry :([/QUOTE]

This is why I explained how to install the latest version ;)
Anyway thank you very much for the great work of the backport team :)

---

### Post by neyz on 2005-07-22
[QUOTE=ghostintheshell]This is why I explained how to install the latest version ;)
Anyway thank you very much for the great work of the backport team :)[/QUOTE]

Heh, just for this kind of situation where some people would like to have a newest version not available in breezy, could you show us how to build a .deb package from sources or point to a nice HOWTO ?

Thanks alot  :D

---

### Post by manicka on 2005-07-22
[QUOTE=neyz]Heh, just for this kind of situation where some people would like to have a newest version not available in breezy, could you show us how to build a .deb package from sources or point to a nice HOWTO ?

Thanks alot  :D[/QUOTE]
 use checkinstall

./configure
make 
sudo checkinstall

This will build a deb and install the package

---

### Post by ghostintheshell on 2005-07-22
[QUOTE=manicka]use checkinstall

./configure
make 
sudo checkinstall

This will build a deb and install the package[/QUOTE]

If I use *checkinstall* and not *make install *that means that I can share the .deb file with other users? And what about linked/missed libraries (needed during the compilation)? Also what about necessary external applications?

Tx, that can help the geeks we are :)

---

