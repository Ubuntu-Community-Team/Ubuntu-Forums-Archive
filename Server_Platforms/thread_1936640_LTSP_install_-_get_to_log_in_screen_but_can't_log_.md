---
title: "LTSP install - get to log in screen but can't log in..?"
date: 2012-03-06
forum: Server Platforms
---

### Post by iangarforth on 2012-03-06
Hi all,

I've been battling and struggling to install LTSP on an 11.10 server, and finally seem to have got somewhere - the client now boots and picks up the Ubuntu thin client profile, and waits there happily to have a username and password entered.

The problem is, this is as far as I get.  If I log in with my main user (the one I put in in the install process) it hangs - the screen changes resolution, but then I get a black rectangle bleeding over the splashscreen with a Linux prompt, but can't type anything.

Typing in any other username (I only have one other user account on the box - commsoffice1) creates the same behaviour as typing in the wrong username or password - it says: 'Response from server - restarting' and then goes back to the log in screen.

What might I be doing wrong?

---

### Post by iangarforth on 2012-03-06
Further to this, I get exactly the same problem on a second (different spec) client - it picks up the profile, waits for the login, and on logging in as my 'main' username, it hangs, whereas any other username is returned to the log on screen.

I think I must be missing something obvious..?

---

### Post by Exonimus on 2012-03-08
I'm not sure what might be wrong, but it might be helpful for other people to have you try adding other user accounts to the server first and have those login on the client. Could you try that and see what happens?

---

### Post by iangarforth on 2012-03-08
Well, I guess I've made something approaching progress.  Not much though...

I installed it on one of our massive school spare servers - quad core, 28GB RAM.  Whatever my probs are atm with this, they ain't performance... ;-)

I think these are two very separate errors.  The 'response from server' one is fixed by running the scripts on [this ]("http://ubuntuforums.org/showthread.php?t=1144420")page:

> **Scormen said:**
> On the server, do in this order:
sudo ltsp-update-sshkeys
sudo ltsp-update-image

After that, restart your client.

However, now I can log in with all the users, but get the same result.  The top left corner of the screen goes black, and I can see the regular Linux prompt: commsoffice1@UbuntuServer $, but the cursor isn't flashing, the mouse is still an 'occupied' wheel, and the client is hung.

Thing is, it's clearly allowed the log in; there must have been some sort of connection, because the client has achieved some sort of log in, even if it is hung, and unrecoverable.

It's odd that I now have achieved precisely the same error on two different servers and two different clients.  I think the error must be quite fundamental to have done that.  I'm wondering if it's because I'm running 32 bit server on 64 bit machines?  Could it possibly be that?

---

### Post by iangarforth on 2012-03-08
> **Exonimus said:**
> I'm not sure what might be wrong, but it might be helpful for other people to have you try adding other user accounts to the server first and have those login on the client. Could you try that and see what happens?

Yeah, the server is quite happy for me to log in with my ubuntuadmin account, or my commsoffice1 account - both are fine to log in with on the server.

---

### Post by Exonimus on 2012-03-08
I'm not sure if it could be that (my knowledge is simply too little) but I do remember reading something about compiling special 32 bit client images on a 64 bit server where 32 bit clients are concerned, with sudo ltsp-build-client --arch i386. If that does not help, a general tip seems to be first disabling the 'quiet splash' boot option, thus disabling the logo and replacing it with text, so one can actually see where stuff goes wrong, like so

sudo gedit /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default

edit: I've also read some general black screen issues being caused by unity, might also be worth looking into. If nothing else works, trying to revert to an older ubuntu edition just for comparative purposes seems like a good move, if one believes other forum threads. Not ideal, not handy, but still worth a shot when trying to sort out the problem and nothing else seems to work, I guess.

edit: this thread: [http://ubuntuforums.org/showthread.php?t=1289099&highlight=ltsp+black+screen](http://ubuntuforums.org/showthread.php?t=1289099&highlight=ltsp+black+screen)
would suggest it could also be graphics related. Are all thin client pc's exactly the same model?

---

