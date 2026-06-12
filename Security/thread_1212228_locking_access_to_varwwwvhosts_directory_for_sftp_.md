---
title: "locking access to /var/www/vhosts directory for sftp user"
date: 2009-07-13
forum: Security
---

### Post by into_311 on 2009-07-13
Hello,

Forgive me for my ignorance, but I have tried to follow serveral how-to'ss in the forum here to setup an sftp jail/chroot environment.

our situation is the following:
1) Our company has hired on a third party website design company
2) their website they developed is not working right, and we want to allow them access to change the code and fix the rss feeds, etc.
3) I'm not sure how to lock them down so when they use sftp it will dump them into the /var/www/vhosts/HOSTNAME directory without allowing them to cd to any other directories, and allow them to modify the files ONLY in that directory.
4) I have tried to setup a chroot/jail environment using the following tutorials:

[http://ubuntuforums.org/showthread.php?t=128206]("http://ubuntuforums.org/showthread.php?t=128206") (which only 
worked till I got to the part where it has you extract the examples - I could not find those examples in there to extract).

[http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/]("http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/")  (which worked well, however, I created my chroot path to /var/www/vhosts/HOSTSITENAME/ this puts me in there, but I can't get to the files in /var/www/HOSTSITENAME/.  DO I need to create the chroot path to /var/www/vhosts/ ? I'm concerned about doing that also, because of other production sites running in that directory that we don't want them accidentally modifying in any way shape or form.

I'm not SURE if that is what I need is a chroot/jailed environment or if you have other ideas on how this can be accomplished easily and securely.

However, one requirement I do have is it has to be to sftp or scp using openssh. I cannot get the network admins to open port 21 and allow non-encrypted ftp transmissions....

Your help would be greatly appreciated.

---

### Post by bodhi.zazen on 2009-07-13
I suggest you simply make a new user and let them make their changes directly. Or let them upload the files to their $HOME and you can move them into place.

If that is not possible, have them send you their changes in an archive (tar ball) and you can extract it for them.

If you must give them direct access, use ssh keys and forced commands (allow only scp).

For an example of how to do this see :

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

IMO ssh jails are more hassle then it is worth.

---

### Post by into_311 on 2009-07-15
The problem is, they keep insisting that it's not their code that is the problem. The problem is with an fopen command that their RSS feed is trying to do now. It won't go out to the web and update the feeds, and we keep telling them that htey need to resolve it. But they insist on having full access to that server, which I'm a little nervous about...

Any thoughts/suggestions?  I do like the idea of giving them a shared key and limited commands. But I don't know if that will work for what they need or not. I'm hoping somebody out there would have a clue why the fopen command won't run on the RSS feeds that they have.  Possibly a firewall issue? We have regular port 80 and 443 enabled outboudn for that server and it's also using SPI (stateful packet inspection).

---

### Post by bodhi.zazen on 2009-07-15
Not knowing the details, it is unusual for them to requests full root access.

I suggest you go ahead and trust them, you are after all allowing them to run code on your server and said code could be anything.

If you wish you can use a shared ssh session, ie screen, and watch what they do.

Simply make a back up of your server first, then give them access while you watch.

Afterwords you would revoke their ssh access and can either restore from back up or un-do their changes.

[http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/](http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/)

---

