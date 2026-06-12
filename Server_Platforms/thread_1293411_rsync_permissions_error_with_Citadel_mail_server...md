---
title: "rsync permissions error with Citadel mail server...how do I fix this"
date: 2009-10-17
forum: Server Platforms
---

### Post by greavette on 2009-10-17
Hello,

I've installed Citadel mail on my Ubuntu Hardy Server VM and I have another Citadel mail running on another PC.  I'm planning on the VM to be my backup mail server and I would like to setup a cron job to copy my /usr/local/citadel/ from my PC to the VM.  This folder contains all I need for citadel mail.

My rsync job looks like this:

```
rsync -va /usr/local/citadel/ myid@192.168.x.xxx:/usr/local/citadel/
```

The problem is that the id I'm using doesn't have the permissions on my VM to copy this folder.  What do I do?  Do I change the permissions on the /usr/local/citadel/ folder or is there another id I'm supposed to use when copying Citadel files?

I know I can transfer as root, but to do this I need to set a root password on my VM first.  I didn't think this was a good idea to set a root password though.

Please advise what's the best route to get this working. 

Thanks!

---

### Post by samosamo on 2009-10-17
Definitely do not change the permission on that directory.  If your environment allows it, the easiest way is to enable the root password and also enable root to log in via ssh.  Ubuntu frowns on this and considers it bad practice.  If you want to do it right you need to use "sudoedit" to modify the sudoers file to allow your rsync user to run rsync as root without a password.  After, use the --rsync-path option so it uses "sudo rsync" instead of the default "rsync". You should also set up passwordless ssh keys and lock it down to the host you're rsyncing from so if anyone gains access to your ssh keys they still can't log in, unless they compromise that host.

If you need more specific examples try googling for things like "passwordless rsync"

---

### Post by greavette on 2009-10-17
Thanks very much for the reply!

I've added my userid to the sudoers file on my VM mail server.  I then issued the following rsync command:

```
rsync -va --rsync-path=/usr/local/citadel/ myid@192.168.x.xxx:/usr/local/citadel/
```

but I received this error:

> bash: /usr/local/citadel/: is a directory
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: remote command could not be run (code 126) at io.c(454) [receiver=2.6.9]

So then I tried issuing the original rsync command again:

```
rsync -va /usr/local/citadel/ myid@192.168.x.xxx:/usr/local/citadel/

```
But I again get permission errors.  

Not sure what I did wrong?  Any ideas.

---

### Post by greavette on 2009-10-17
To see if using my root account would allow me to rsync the folder to my VM, I created a password for my root account:

```
sudo passwd root
```

Then used the following command to rsync my folder to my VM:

```
rsync -va /usr/local/citadel/ [email]root@192.168.x.xxx[/email]:/usr/local/citadel/

```
It prompted me for my root password on the VM and ran without a problem.  I was able to copy my folder over with no trouble.  Fired up my Citadel mail server on the VM and all my mail and settings were there.  

So can anyone tell me why it works for my root account and not for my userid even though I've added my userid to my sudoers file?  

I agree with samosamo that I don't want to touch my permissions on my citadel mail folder.  What else can I do?

I had planned on using public keys (passwordless rysnc) eventually but I don't think that will work either if I can't use my own userid with the rsync command.  I don't really want to add a password to my root account, but it would seem I have too.  

Any help you can provide would be greatly appreciated.

---

### Post by samosamo on 2009-10-17
Wrong syntax, --rsync-path is to define the path to the rsync executable.  for example:

```
sudo rsync -av --progress --rsync-path="sudo rsync" /home user@backupbox:/backups/
```

But since you are enabling the root account there is NO NEED for sudo.  Choose one solution only.

Also I mentioned earlier that by default the root account is not allowed to ssh.  You need to enable that in the ssh config.

---

### Post by greavette on 2009-10-17
I see...I googled for --rsync-path but didn't understand how to use it.

I haven't enabled root access through ssh since I'm not using ssh to do this transfer yet...at least I don't think I am?  Or does this code:

```
myid@192.168.x.xxx:/usr/local/citadel/
```

imply ssh?

I would rather use my own id (and not root) to transfer my files.  I added a password for root only to test that my rysnc would work for root...not to use two solutions.  Once I get this working I'll create a new VM and not create a password for root.  So here is my revised rsync command:

```
sudo rsync -av --progress --rsync-path="sudo rsync" /usr/local/citadel/ myid@192.168.x.xxx:/usr/local/citadel/
```

This results in asking for my password for the VM and then prompts for another password?  I'm not sure what password to type next so I try typing my VM password again, but now I can see what I type...it's not hidden.  Then it just hangs and nothing happens.

Sorry for asking so many questions but I'm obviously I'm still not understanding how to use this?  I very much appreciate your help!

---

