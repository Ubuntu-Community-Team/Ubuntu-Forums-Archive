---
title: "Is validation all in the UID?"
date: 2009-07-03
forum: Security
---

### Post by Lucky. on 2009-07-03
This is likely old hat to all of you, but it's got me bothered until I know what the common solution is to it.

Here's an experiment I performed...

1.  I set up a server, and of course the first user account I created was "Lucky" with a password "blahblah".  The server assigned him the UID of 1000.

2.  I set up a client, and of course the first user account I created was "Lucky" with a password "blahblah".  The client assigned him the UID of 1000.

3.  Using the client, I connected to an NFS share on the server.  The NFS share had bits 0700 on the directory...so only the owner (which was "Lucky") could have any access to it.

4.  I connected fine, and had full access..

Then I got to thinking...what type of validation was happening here?  What happened if I changed the password on my client?  Could I still connect?

1.  I changed the password on the client from "blahblah" to "yupyupyup".  I rebooted, and logged in.

2.  I was still able to access the NFS share with full permissions!  That's a little creepy.  My password was "wrong".

This got me thinking a little more.  What if my name was differently entirely?

1.  I reformatted with a new client, and had its first user be "somedude" with a password "somepassword".

2.  I was still able to access the NFS share with full permissions...

3.  I added a user called "Lucky", with a password of "blahblah".  He couldn't access the share.  Even though his name and password were correct, no worky.

GAH!

So I'm assuming that validation is merely a UID and/or a GUID thing.  If I want to access a share, I send out my UID.  Who cares what my name is or what my password is.  If I can supply the correct UID, I'm in good shape.  In fact, forget guessing UIDs.  If the root account is enabled, I imagine that's the same UID on most systems.

On the surface, this seems dreadfully wrong...a recipe for a brute force attack to any network share.  I know you can limit IP addresses and whatnot with NFS, but that still wouldn't protect from an internal attack.

My questions are:

1.  Short of disabling the root account, how can you protect from a brute force attack where a client simply tries to access a share using a few thousand UIDs?

2.  Wait a minute...how am I supposed to access the files on my server without taking care to match UIDs on the client?  If Lucky is user #1 on the server and user #5 on the client...he can't get to the share.  That seems ridiculous.  What service to people use for client/server validation?  I've caught glimpses of things like people replicating passwd files or something like that...or using NIS?  I dunno.

Thanks a bunch, and sorry if this all seems comical.  It's a surprise to me, and I'm very curious on how people deal with it.

---

### Post by The Cog on 2009-07-03
You have got it right. I set up an NFS server for the first time last week, and found out for myself then. 

It it possible to do user id mapping in an environment where userids are not coordinated. See [http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports) .

P.S.
This looks handy, too:
[http://tldp.org/HOWTO/NFS-HOWTO/index.html](http://tldp.org/HOWTO/NFS-HOWTO/index.html)

---

### Post by Agent ME on 2009-07-03
If you're looking for security, NFS is the wrong answer.

NFS is good when all of the systems connected are properly locked down and share the same user list.

---

### Post by Lucky. on 2009-07-03
> You have got it right. I set up an NFS server for the first time last week, and found out for myself then.

It it possible to do user id mapping in an environment where userids are not coordinated. See [http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports) .

P.S.
This looks handy, too:
[http://tldp.org/HOWTO/NFS-HOWTO/index.html](http://tldp.org/HOWTO/NFS-HOWTO/index.html)


Thanks, I looked at those, and then some more.  It appears as if Kerberos is the way to go in order to get the security I want, but it does seem to be a little overboard...and I can't find any decent tutorials.

> If you're looking for security, NFS is the wrong answer.

NFS is good when all of the systems connected are properly locked down and share the same user list.

If NFS isn't the answer, what is the right answer?  Please don't say Samba...

---

### Post by Agent ME on 2009-07-03
I'm not too sure, but Ubuntu does use Samba as default if you right-click and share a folder, so it doesn't seem Samba is too bad. Guess it matters what the use is.

---

### Post by koenn on 2009-07-04
> **Agent ME said:**
> I'm not too sure, but Ubuntu does use Samba as default if you right-click and share a folder, so it doesn't seem Samba is too bad. Guess it matters what the use is.
Ubuntu supports samba mainly on the assumption that 
a/ its users also use windows, and need a way to share files with other windows computers;
b/ its users are ex-windows users and look for windows-like replacements first, before considering unix-like solutions

> **Lucky. said:**
> 
So I'm assuming that validation is merely a UID and/or a GUID thing.  If I want to access a share, I send out my UID.  Who cares what my name is or what my password is.  If I can supply the correct UID, I'm in good shape.  In fact, forget guessing UIDs.  If the root account is enabled, I imagine that's the same UID on most systems.
you're right about the UID thing. This is a known and documented property of NFS : [http://nfs.sourceforge.net/nfs-howto/ar01s06.html](http://nfs.sourceforge.net/nfs-howto/ar01s06.html)

NFS security assumes that there's a sysadmin who has root on servers, and mere users connect from terminals and workstations where they are not root and can't su. That would be appropriate in the computer environments where NFS was designed, in corporate networks, etc, but it doesn't sit well with the home user situation who can get root/sudo  on his PC. 
NFS basically exports a filesystem, and assumes the access control is managed on the client : simple and straightforward, but it only works well if all clients are also managed by the sysadmin.

Root always has UID=0. so a user who can get root on his workstation, would have root file access on the server.
NFS deals with this with the "root_squash" option, so that a client with root becomes "nobody" on the server. This can also be used to protect files : if they are only readable/writable by root on the server, they will never be accessible by an NFS client.

Other than that, you need to build up layers of security :
- control who has access to your server (firewall, tcpwrapper, ...). typically, this would be limited to your LAN, and you know which computers and users belong there. 
- control what you export, to which hosts, and with which options (ro, rw, squash, no suid, ...). You may need to make eg separate exports of subdirs, and set specific options for each,  in stead of exporting the entire parent dir to all clients.
- control what user accounts exist on what host (combined with 'which hosts you export to', this goes a long way in managing file access), preferably with consistent UIDs across hosts

it's the combination of those that makes up nfs security, not the properties of NFS as such.

> **Lucky. said:**
> It appears as if Kerberos is the way to go in order to get the security I want, but it does seem to be a little overboard...and I can't find any decent tutorials.
Centralised user management, Kerberos , ... would seem the way to go in a large environment. Also look at secure NFS / secure RPC. I think NFS v4 is meant to incorporate those.

For a small number of users / computers, manually setting consistent UIDs acros all accounts on all computers may, if combined with other measures explained earlier,  be an acceptable solution. The 'squash' examples in man exports (re Cog's post) may help, eg when dealing with user home dirs or a similar situation

> **Lucky. said:**
> 
If NFS isn't the answer, what is the right answer?  Please don't say Samba...
It's up to you to decide whether NFS is the right answer, but you should take an informed decision, i.e. understand the security issues and practices involved, and work out a solution that works for you.

you might also want to look at ssh/sftp and sshfs mounts. [http://en.wikipedia.org/wiki/SSHFS](http://en.wikipedia.org/wiki/SSHFS) the same remarks apply : see how it works and what is required to do it securely, then see if that works for you.

---

### Post by scorp123 on 2009-07-04
> **Lucky. said:**
>  3.  Using the client, I connected to an NFS share on the server.  The NFS share had bits 0700 on the directory...so only the owner (which was "Lucky") could have any access to it.

4.  I connected fine, and had full access.. NFS is supposed to work like that.

> **Lucky. said:**
>  what type of validation was happening here? What type of validation is happening when you insert a harddisk into your computer? None. Same thing here. Except that the "harddrive" is not connected via IDE-, SCSI, or SATA cables but via TCP/IP.

If you want a more restrictive setup you could always limit the IP's that are able to connect to the NFS share. And using options such as "root_squash" wouldn't be a bad idea too.

See here:
[http://ubuntuforums.org/showpost.php?p=4184680&postcount=122](http://ubuntuforums.org/showpost.php?p=4184680&postcount=122)

> **Lucky. said:**
>  What happened if I changed the password on my client?  Could I still connect?  Of course. See above: Just as if you had added an internal harddisk .... That's NFS. Except you connect to it via the network.

Some people compare NFS to SAMBA ... but that's like comparing apples and oranges. NFS is a totally different beast that's best compared to an _internal_ disk. Because that's where its origins are: When harddisks were expensive and rare, admins would use NFS to share a server's harddisk between multiple diskless client devices. Hence the behaviour of NFS ... it behaves exactly like an internal disk would. No authentication, no passwords, nothing. If you own an UID you also own the directories and files on a NFS share that belong to that UID ... Just as you would on an internal disk too.

> **Lucky. said:**
>  That's a little creepy.  No it's not. NFS works as intended.

> **Lucky. said:**
>  My password was "wrong".  NFS doesn't care about your password.

> **Lucky. said:**
>  If the root account is enabled, I imagine that's the same UID on most systems.  "root" is always UID=0. But see above. To make sure nobody can pretend to be "root" on a NFS share you'd use "root_squash" in the mount options. See the link I posted above.

> **Lucky. said:**
>  but that still wouldn't protect from an internal attack.  "NFS" and "security" are two mutually exclusive terms :)

> **Lucky. said:**
>  Short of disabling the root account, how can you protect from a brute force attack where a client simply tries to access a share using a few thousand UIDs?  How about using SSHFS? All that needs to be open on the server is SSH. And from the server's point of view it's a SSH connection. From the client's or end-user's point of view it will look like NFS. It's dead easy to use.

I see others already suggested SAMBA (I hate SAMBA ... it's so Windows-ish) and Kerberos (baaaaaaaah!!! Good luck with that. It's a royal PITA to set that one up, IMHO ...).

SSHFS is dead simple to use. All you need to have is a valid username and password on the remote system. And UID and GID don't matter at all. What matters is how you authenticated on the target system.

Give it a try. :)

---

### Post by Lucky. on 2009-07-04
Guys, thanks for the good advice.  Before I read this, I had already implemented DNS, DHCP, Autofs, NFS, and Kerberos.  However I still hadn't gotten DHCP to auto-update DNS, and my clients weren't authenticating very well with Kerberos without command line help.

In the back of my mind while I've been doing all of this, I keep thinking of ways to efficiently implement this into my workplace.  I would love to replace the 50 workstations at work with Linux...or even just a Linux server for starters.

I installed sshfs, and it's almost working 100%.  Indeed it's a great solution for a home network.  But there's one catch:

If I use Gnome's "Connect To Server" on the client to get to the share, the umask I have specified in /etc/profile goes out the window.  In fact...the umask for the server goes out the window too.  On both client and server, the umask is 007.  However it appears that when I use Gnome to connect, I get a umask of 022.

If I use the command prompt to mount a share, I get the a mask of 007.  But not if I connect through gnome.

Any clues besides setting up entries and options in fstab or autofs?  I understand both, but I'm looking for a more elegant solution.

(I figured this question may be suited better in its own thread as it's strayed from this thread's subject.  Links is below.)

[http://ubuntuforums.org/showthread.php?p=7563057](http://ubuntuforums.org/showthread.php?p=7563057)

---

