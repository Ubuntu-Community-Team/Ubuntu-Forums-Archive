---
title: "SSH not remembering keys?"
date: 2012-03-27
forum: Security
---

### Post by NertSkull on 2012-03-27
So lately on one computer I've been having some issues with SSH.  I have it set up with SSH key pair authentication (no password login).

Lately, I have to restart SSH on the server computer every few hours or I can't login.  When I try, I get the message that I can't be authenticated (pubkey).

But if I simply do /etc/init.d/ssh restart, then everything works again and I can login from the client.

Its getting a little old to have to call home every few hours to restart ssh.

Anyone have any ideas of how I can troubleshoot this more?  I've been using SSH for years and never had this issue.

---

### Post by CharlesA on 2012-03-27
What version of Ubuntu are you using? I haven't run into that on my Lucid box(es).

---

### Post by kevdog on 2012-03-27
This problem happened to me once in yesteryear, I think I just purged and reinstalled and the problem went away.  I think I also had some conflict with another listening process .. I really can't remember, but if desperate -- dumbify your setup.

---

### Post by NertSkull on 2012-03-28
My server is on Maverick (10.10).  Its really random when it happens.  But everytime just restarting ssh solves the problem.  So I don't think it appears to be an issue with file locations or anything.

And because its random when it happens, I really have no idea how to troubleshoot it.  I may re-install here, but ideally I'd like to figure out whats happening first just in case it ever happens again.  So I'm going to hold off on that for a bit until maybe I see a pattern or something that makes more sense.

---

### Post by CharlesA on 2012-03-28
It would just be a hiccup. If purging and reinstalling openssh-server doesn't fix it, the next step would be to see if the same thing happens if you try to connect to localhost from that box.

---

### Post by NertSkull on 2012-03-30
So, I've purged and reinstalled ssh and I'm still getting the same issue.  It tells me "Permission denied (publickey)".

But if I have someone at home restart ssh (/etc/init.d/ssh restart) I can immediately get back in with no problem.  Any ideas on how to figure this out?

Also, when it denies me, I've tried logging in with my freenx server.  And the "nx" user can get in.  But once it tries to do the second part, it fails there as well.

---

### Post by CharlesA on 2012-03-30
Odd.

Have you tried recreating the keys?

---

### Post by NertSkull on 2012-03-30
No, not yet.  I'll do that and see if it fixes the problem.

---

### Post by NertSkull on 2012-04-02
No go!  I regenerated the keypair and I'm still having the same issues.  The server denies me, but a simple restart and I get back in.

I'm not sure what the next step should be.

---

### Post by CharlesA on 2012-04-02
Try starting sshd in debug mode and see if it has the same problem:

[http://ubuntuforums.org/showpost.php?p=10436923&postcount=7](http://ubuntuforums.org/showpost.php?p=10436923&postcount=7)

---

### Post by NertSkull on 2012-04-03
Allright, I'm about 98% sure I've figured it out.  I'll test it here for a week or so and see if I have the problem resolved.  

I never thought about it, but it turns out that when you have your home directory encrypted, it encrypts the authorized_key file (obviously) and so sshd can't read that until you are logged in.  Which you can't login until it can read the file.

So I moved my authorized key file elsewhere, and I suspect that will take care of it.

It ends up not being restarting ssh that was fixing the problem before.  But I was always having my wife fix it from her account.  And she would use the terminal to login as me (su nertskull) and then restart ssh.  But it wasn't the restarting that fixed it, it was logging in as me first that opened up that file to be read.

The part I'm still a little confused on is this.  When she logged out of the terminal, I could still login for a few hours.  Does the /home directory encryption not kick back in for a little bit afterwards?  Does it keep you decrypted for a period of time after logging out?

---

### Post by CharlesA on 2012-04-03
If your home directory is encrypted, then moving the authorized_keys file and pointing sshd_config to that location is the fix.

I'm not exactly sure how the whole processes of encrypting/decrypting your home directory work but I've read that it's supposed to be doing "silently" and "in the background" after the user logs in or out.

---

### Post by NertSkull on 2012-04-04
Yeah, it appears to have fixed the issue.  So I'm marking as solved.

I'd still be curious to know why the delay.  But thanks for the help.

---

### Post by CharlesA on 2012-04-04
I'm curious about that as well. It seems quite odd. Are you sure the machine was logged out instead of just locked?

---

### Post by NertSkull on 2012-04-06
Yeah it was definitely logged out.  

I'm not 100% positive, but I found this bug ([https://bugs.launchpad.net/ecryptfs-utils/+bug/706078](https://bugs.launchpad.net/ecryptfs-utils/+bug/706078)) that I think kind of addresses it.  Something about pam keeping a cache or something.  Not sure that's the problem, but I know its working now by moving the location of authorized keys.

---

### Post by CharlesA on 2012-04-06
Interesting bug report.

Glad you got it working.

---

