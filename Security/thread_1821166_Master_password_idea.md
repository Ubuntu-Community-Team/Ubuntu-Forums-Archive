---
title: "Master password idea"
date: 2011-08-08
forum: Security
---

### Post by kerryhall on 2011-08-08
I have a lot of different passwords for various websites and accounts and such. I was considering consolidating them into a plaintext file, then encrypting that file with:

openssl aes-256-cbc -salt -in passwords.txt -out passwords.enc

Then shredding passwords.txt afterwords. The only holes in this idea I can think of is that the plaintext file might get cached or kept in memory somewhere, or that the filesystem makes a backup, and if I cat the plaintext file, I would have to purge bash's scrollback buffer.

But if those are taken care of, any other reason why this would be a bad idea? 

Thanks!

---

### Post by JASONFUSARO on 2011-08-08
I posted a password scheme:

[http://ubuntuforums.org/showthread.php?t=1812501](http://ubuntuforums.org/showthread.php?t=1812501)


If you can program then you can make the text file as large as you want, don't even have to hide it say 80 thousand characters long and your program or script can pull out just the section you want, only you will know it, for a simple example: the program would accept input your input and pull out what only you know is the position in the file say 100 characters and your password is 6 to 20, it pulls it out you copy and paste it. Now if the text file is say 80,000 characters and your password is in their somewhere only you know, I don't see how anyone can determine what it is, they would first have to know how long it was and even then I think the permutations would be extreme.

People out their know how the Crypto schemes function, knowing that they have a start, you need something only you know and and random output. You pick the location, no one will ever know that, no on will have a place to start, unless they hypnotize you, to extract the location.


Just a thought

---

### Post by bodhi.zazen on 2011-08-08
> **kerryhall said:**
> I have a lot of different passwords for various websites and accounts and such. I was considering consolidating them into a plaintext file, then encrypting that file with:

openssl aes-256-cbc -salt -in passwords.txt -out passwords.enc

Then shredding passwords.txt afterwords. The only holes in this idea I can think of is that the plaintext file might get cached or kept in memory somewhere, or that the filesystem makes a backup, and if I cat the plaintext file, I would have to purge bash's scrollback buffer.

But if those are taken care of, any other reason why this would be a bad idea? 

Thanks!

You can do that.

As an alternate you could consider keepassx It is in the repos and you can run it (cross platform) from a flash drive.

Someone mentioned a firefox extension for it, but I have  not tried that.

---

### Post by tubbygweilo on 2011-08-09
Another vote for Keepassx - it works as advertised and works right out of the repos.

---

### Post by FuturePilot on 2011-08-09
We already have this. It's called Keepass(x)

---

### Post by sneakyimp on 2011-08-09
Has anyone here personally verified the signature on the Keepass(x) repository?  Your security is only as good as its weakest link.

---

### Post by kerryhall on 2011-08-16
> **sneakyimp said:**
> Has anyone here personally verified the signature on the Keepass(x) repository?  Your security is only as good as its weakest link.

I'm wondering about this myself. Has the code been audited for security holes? I guess my concern applies to pretty much any security related piece of ubuntu software (and possibly all software). Is there a web site that concerns ubuntu security, and has logged audits of code to assure us that yes, various things like openssl and keepassx are secure?

Thanks!

---

### Post by sneakyimp on 2011-08-16
This might just bum you out, but look in **/etc/dpkg/dpkg.cfg** and you'll see this:
```
# Do not enable debsig-verify by default; since the distribution is not using
# embedded signatures, debsig-verify would reject all packages.
no-debsig
```

I tried to get some more information on the exact implications of this on the #ubuntu IRC channel, but just got griefed by the folks there.  Answers were mostly "you should be more worried about other stuff like your web stack" and "do you have any idea how hard it is to get something into a repository?"

I would very much like to draw more attention to this so that perhaps the devs will get serious about insuring security.

---

