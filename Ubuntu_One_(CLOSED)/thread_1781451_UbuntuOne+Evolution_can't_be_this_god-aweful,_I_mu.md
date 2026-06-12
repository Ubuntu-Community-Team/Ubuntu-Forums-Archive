---
title: "UbuntuOne+Evolution can't be this god-aweful, I must be doing something wrong."
date: 2011-06-13
forum: Ubuntu One (CLOSED)
---

### Post by prawnstar on 2011-06-13
(Natty 11.04)

When trying to copy my personal address to CouchDB I get this error:
- - - - - - - - - -
Unable to open address book

This address book cannot be opened. This either means that an incorrect URI was entered, or this server is unreachable.

Detailed error message: Invalid source
(ok)
- - - - - - - - - -


I have been trying (since 10.04!) to sync my Evolution contacts. UbuntuOne seems to be the most promising way of doing that automatically, however, I completely fail at accomplishing this seemingly simple task. I have NEVER been able to successfully back up my address book to UbuntuOne. Note: all other sync works fine. It's just Evolution that is seemingly smarter than I am.

Thing I have done to solve the issue:

- Upgraded from 10.04 to 11.04
- All three steps from this article:
[https://wiki.ubuntu.com/UbuntuOne/FAQ/WhyArentMyContactsInEvolutionSyncing](https://wiki.ubuntu.com/UbuntuOne/FAQ/WhyArentMyContactsInEvolutionSyncing)
- Cuss and swear and roll my eyes, mutter a few unrepeatable curse words about Canonical and their mothers.


None of this has solved my issue. Any help is GREATLY appreciated.

Thanks!

---

### Post by gsimpson on 2011-06-14
Go to package manager. Is evolution-couchdb installed?

---

### Post by David Crockett on 2011-06-14
Hi,

I have the same issues and I have evolution-couchdb installed.  couschdb desktop tools  tell me that it is paired with ubuntu one.   Interestingly I had one contact on Ubuntu one that I entered manually show up in my evolution contacts.   But the other direction does not work.    

Regards,
DC

---

### Post by duanedesign on 2011-06-15
First I would try the steps under [killing and restarting desktopcouch]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting"). Step 4, opening the Futon interface in your browser, will just confirm desktopcouch is running. Once you have confirmed it is running see if you still get errors trying to access the U1 address-book.

If you still get errors, I think you have done this, but make sure evolution-couchdb is installed. If so, can you please quit evolution and then go to a terminal and run the following:

$ killall -9 e-addressbook-factory
$ export COUCHDB_DEBUG_MESSAGES=1
$ /usr/lib/evolution/e-addressbook-factory

then, open Evolution and try to open the U1 addressbook again. When it fails again, please go back to the terminal and paste all the output from the last command to this thread?

---

### Post by DarrenO on 2011-06-21
I followed this help here and was able to get the U1 contacts list stop giving me an error whenever I tried opening it. So now I have one contact in my Evolution Ubuntu One list and one contact in Ubuntu One, but they are different contacts and the syncing does not seem to work.

No idea where to go from here. Wait until there is a patch?

---

### Post by briancb on 2011-06-22
I too am getting distraught with U1. I have tried everything advised. The last message I got in evolution was:

Unable to open address book

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._e_2ddata_2dbook_2derror.Code100: Cannot open book: Could not create DesktopcouchSession object

Also got this in terminal

** (e-addressbook-factory:2491): WARNING **: Couldn't get desktopcouch port: GDBus.Error:org.freedesktop.DBus.Python.RuntimeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/ipc.py", line 50, in getPort
    port = int(direct_access_find_port(ctx=self.ctx))
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/__init__.py", line 172, in direct_access_find_port
    return direct_access_find_port(pid, ctx, retries_left - 1)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/__init__.py", line 172, in direct_access_find_port
    return direct_access_find_port(pid, ctx, retries_left - 1)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/__init__.py", line 172, in direct_access_find_port
    return direct_access_find_port(pid, ctx, retries_left - 1)
  File "/usr/lib/pymodules/python2.7/desktopcouch/application/platform/linux/__init__.py", line 173, in direct_access_find_port
    raise RuntimeError("Unable to find listening port")
RuntimeError: Unable to find listening port

---

### Post by muzikayise on 2011-12-02
> **duanedesign said:**
> First I would try the steps under [killing and restarting desktopcouch]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/Troubleshooting"). Step 4, opening the Futon interface in your browser, will just confirm desktopcouch is running. Once you have confirmed it is running see if you still get errors trying to access the U1 address-book.

If you still get errors, I think you have done this, but make sure evolution-couchdb is installed. If so, can you please quit evolution and then go to a terminal and run the following:

$ killall -9 e-addressbook-factory
$ export COUCHDB_DEBUG_MESSAGES=1
$ /usr/lib/evolution/e-addressbook-factory

then, open Evolution and try to open the U1 addressbook again. When it fails again, please go back to the terminal and paste all the output from the last command to this thread?


thanks this worked for me. I'm using ubuntu 11.10

---

