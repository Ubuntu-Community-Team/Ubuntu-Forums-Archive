---
title: "Chkrootkit suspicious files etc"
date: 2010-11-08
forum: Security
---

### Post by ianc1 on 2010-11-08
I ran chkrootkit today and my quantity of suspicious files/dirs is rapidly growing I now have:

/usr/lib/jvm/.java-6-openjdk.jinfo
/usr/lib/xulrunner-1.9.2.12/.autoreg
/usr/lib/thunderbird-3.1.6/.autoreg
/usr/lib/firefox-3.6.12/.autoreg
/usr/lib/python2.6/dist-packages/enthought/tvtk/html/.buildinfo
/usr/lib/python2.6/dist-packages/enthought/mayavi/html/.buildinfo
/usr/lib/python2.6/dist-packages/enthought/docs/html/tvtk/.buildinfo
/usr/lib/python2.6/dist-packages/enthought/docs/html/mayavi/.buildinfo
/usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path

I know that some of these are false positives like the first java one and the xulrunner, and I assume Firefox and Thunderbird.  But what's with all the python ones?  Can anybody enlighten me?

That's a lot of suspicious files to check in one go.  Last week the quantity was much less.  A quick google for chkrootkit and enthought has yielded nothing.

Any ideas?

---

### Post by epz on 2010-11-08
I googled it too very quickly. It may be one of these :

This is from Wikipedia (i dont know if i'm allowed to post links)

The Enthought Tool Suite include:
Traits: A manifest type definition library for Python that provides initialization, validation, delegation, notification, and visualization. The Traits package is the foundation of the Enthought Tool Suite, underlying almost all other packages. It includes:


TraitsUI: A GUI support for Traits-based objects, supporting a Model-View-Controller architecture. It is currently based on the wxPython toolkit.


VET: View Editing Tool, for building Traits user interfaces.


TVTK: Traits-based wrapper for VTK, a 3-D Visualization Toolkit.


MayaVi: 2-D/3-D scientific data visualization, usable in TraitsUIs as well as an Envisage plug-in.


Envisage: An extensible plug-in architecture for scientific applications, inspired by Eclipse and NetBeans in the Java world.


Enable: A multi-platform DisplayPDF drawing engine that supports multiple output backends, including Windows, GTK, and Macintosh native windowing systems, a variety of raster image formats, PDF, and PostScript.


Chaco: An interactive 2-D plotting toolkit for Python.


Endo: An API documentation formatter that supports Traits-based code by extracting both docstrings and attribute assignment comments. It uses the DocUtils package and outputs to HTML.


Or some other maths related software using python.

---

### Post by cariboo on 2010-11-08
What scientific packages that use enthought python have you installed lately?

---

### Post by ianc1 on 2010-11-08
Ahh should have explained I've installed enthought and pyqt4 and Mendeley which uses Qt4.  So I know these files exist the query is why are they suspicious?

I've ran rkhunter as well it doesn't identify these as issues but informs me the hashes of last, awk, ldd (in /usr/bin) and many other files have changed.  I can only assume this is an update issue ie they have and should have changed.  However downloading the packages for Meerkat that contain awk, last and ldd and extracting these three files and checking the md5sum, shasum, sha1sum, sha256sum they do not compare with rkhunters currently stored hash.

On a side note is there a better way of doing this than identifying the corresponding package, downloading, extracting and hashing?

Cheers

---

### Post by epz on 2010-11-08
> **ianc1 said:**
> Ahh should have explained I've installed enthought and pyqt4 and Mendeley which uses Qt4.  So I know these files exist the query is why are they suspicious?



Cheers

Guess, as you can see every file has a dot before, that means it's a hidden file that chkrootkit may have reported as threat, false positives i guess.. I can't swear it but it's most likely to be so.

---

### Post by cariboo on 2010-11-09
I have to ask why you are running rkhunter and chkrootkit, do you have a suspicion  that your system has been broken into?

A competent cracker usually doesn't leave anything that either tool will find. The last rootkit I played with didn't show up using either tool.

---

### Post by ianc1 on 2010-11-09
I simply run both rkhunter and chkrootkit as a double check.  I run both utilities weekly and try to keep on top of the warnings/suspicious entries.

Would the advice be to run only one of these utilities and if so which one?  I note that Canonical only provide critical security updates to chkrootkit.

I do appreciate that a good hacker would leave no trace.  In that case one could argue that there is no point to run either program and one is simply fighting a loosing battle.

On the matter of checking hashes for rkhunter even if I stop using it I would like, as a learning exercise, to understand where I went wrong.  I can see no error in downloading the packages for the Meerkat packages extracting the relevant file(s) and checking the hash.

Cheers

---

### Post by cariboo on 2010-11-09
If you are only using packages from the repositories, you don't have to worry about compromised packages, as it is pretty hard for joe-random-cracker to access them due to the checks and balances in place to gain the privilege.

If you want to learn more about what it takes to become a developer, and why we trust the packages in the repositories, you can start [here]("https://wiki.ubuntu.com/UbuntuDevelopers").

---

### Post by ianc1 on 2010-11-09
Sorry.  I'm not questioning the integrity or security of the applications in the repository.  However isn't it feasible for me to get a rootkit via other means?  eg whilst I don't just download and install random software from the web there are the odd ones I want/need.

I also like to try and determine why packages installed through the repository have files/directories which appear as suspicious.  In this case for example the Enthought package which I trust came from the repository but some of its directories are identified as suspicious.

---

### Post by brian_p on 2010-11-09
> **ianc1 said:**
> 

However isn't it feasible for me to get a rootkit via other means?  eg whilst I don't just download and install random software from the web there are the odd ones I want/need.

It is feasible but chkrootkit (or rkhunter) will do nothing for you. It you examine what it is looking for and how it goes about it you will see it would struggle to detect any malware of consquence.

> I also like to try and determine why packages installed through the repository have files/directories which appear as suspicious.  In this case for example the Enthought package which I trust came from the repository but some of its directories are identified as suspicious.

Basically you would be spending your time on determining why chkrootkit got it wrong. Producing false postives is its normal mode of operation.

---

### Post by ianc1 on 2010-11-09
Coming from a Windows backgound I am used to firewalls, virus checkers, intrusion detection etc.  I run ClamAV and a firewall but maybe feel reassured by the use of rootkit detection.

Is there an alternative approach to this.  I know I could switch of the router!

---

### Post by brian_p on 2010-11-09
> **ianc1 said:**
> Coming from a Windows backgound I am used to firewalls, virus checkers, intrusion detection etc.  I run ClamAV and a firewall but maybe feel reassured by the use of rootkit detection.

Reassurance is about all you will get. Don't expect protection.

> Is there an alternative approach to this.  I know I could switch of the router!

The standard approach works very well: update regularily and get software from known, trusted sources. Use root privileges only for essential administrative tasks.

---

### Post by ianc1 on 2010-11-11
Thanks brian_p I was wondering if that was the case.

Does anyone have any feelings as two which of rkhunter/chkrootkit I am better using if any?

---

### Post by cariboo on 2010-11-11
The chances of getting a root kit/cracked are pretty slim unless you are running an ssh or remote desktop server with a weak password forwarded to your router.

Chkrookit and rkhunter cause more problems than they solve, with all the false positives.

---

### Post by brian_p on 2010-11-12
> **ianc1 said:**
> 

Does anyone have any feelings as two which of rkhunter/chkrootkit I am better using if any?

You can make your own mind up. Evidence is preferable to what you feel in your waters. 

Go through the nasties these programs are supposed to detect. I'll start you off with three from chkrootkit: Gold2 rootkit, Hidrootkit and Ducoci rootkit. What information can you find out about them? What do you conclude?

Suppose your doctor warned you not take a holiday in Scotland because of the dangers of Gold2, Hidrootkit or Ducoci disease and advised you to drink a glass of unicorn milk a day to ward off contracting them. But nobody in that fair land or anywhere else had any information on these conditions. Would you stay at home?

---

