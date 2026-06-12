---
title: "No &quot;add computer button&quot;"
date: 2010-10-06
forum: Ubuntu One (CLOSED)
---

### Post by PCTinker on 2010-10-06
In an attempt to see if Ubuntu One was the cause of my CPU maxing out I deleted it from the list of machines connected to my One account.

Now I can fidn no way of reconnecting as there is no button saying "add machine to this account"

Is this a bug or am I missing something?

(CPU still maxed out after 10 mins)

---

### Post by PCTinker on 2010-10-06
Problem solved.
I reinstalled the UBUNTUONE-CLIENT. Then when I launched it it took me to the CONFIRM COMPUTER page.

Says to himself "Think before posting":oops:

---

### Post by randumnumber on 2010-10-06
A good reference is here:
[https://bugs.launchpad.net/ubuntuone-client/+bug/363243](https://bugs.launchpad.net/ubuntuone-client/+bug/363243)
First make sure there is no keyring entry by going to
applications>accessories>password and encryption keys>Delete anything pertaining to ubuntuone

Then do this code at terminal:
```

sudo apt-get install ubuntuone-client-tools

u1sync --authorize

```

---

### Post by ratcheer on 2010-10-11
randumnumber, I have the same problem the OP had, except I already have ubuntuone-client installed. So, I tried your suggestion and got the following:

```

tim@tim-mav-prod:~$ u1sync --authorize
Usage: u1sync [options] [DIRECTORY]
       u1sync --list-shares [options]
       u1sync --init [--share=SHARE_UUID] [options] DIRECTORY
       u1sync --diff [--share=SHARE_UUID] [options] DIRECTORY

u1sync: error: no such option: --authorize


```

I do not have a ubuntu one key in my Passwords and Encryption Keys, but when I start Ubuntuone preferences, it will not pop up the Ubuntuone signon dialog. Therefore, I cannot connect.

What to try next?

Tim

---

### Post by ratcheer on 2010-10-11
However, the man page for u1sync says the --authorize option should exist and that it should open a browser window to allow me to ".... conduct the authorization process using your Launchpad credentials and store the resulting token in the gnome keyring." But, it does not.

Tim

---

### Post by ratcheer on 2010-10-11
OK, I have solved my problem, too. The thing was, I did not know how to find and select my ubuntuone authorization key to delete it. I finally found it, deleted it, then the u1 preferences let me add it back.

Tim

---

