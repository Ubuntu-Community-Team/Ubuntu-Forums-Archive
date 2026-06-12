---
title: "ecryptfs mountable by root"
date: 2011-01-23
forum: Security
---

### Post by miticotoby on 2011-01-23
Hi everybody,

   got a quick question:

so I setup an ecryptfs "Private" folder in my home. works great. It automounts on login, unmounts on logout as it should be.

However if I run "sudo -u USER ecryptfs-mount-private" root can mount my private directory without any password being asked. I understand root is root, however if I got it right the "mount-password" should still be encrypted using the users loginpassword so even though I run this as root I should still need to type in the users password

same thing is true if I do a ssh-keybased authentication. The password never gets typed anywhere however the Private folder gets mounted just fine.

is there a way to force even root to type my password to see my unencrypted files?

thanks

---

### Post by Dave_L on 2011-01-23
I think that works only because you're logged in (as the user with the encrypted home). If you reboot in recovery (single-user) mode, which drops you into a root login, you shouldn't be able to mount the encrypted directory.

For test purposes, I created an extra user account with an encrypted home directory.  So I have two users with encrypted home directories.  When logged into either of the users, I can't access the other's unencrypted home directory files, even with sudo.

---

### Post by miticotoby on 2011-01-23
hey, thanks for the quick response.

well the thing is when I tried this I wasn't logged in as the user with the encrypted home. during the test I logged in straight as root (NOT using sudo...) and it still worked

I even waited for about an hour (roughly) to make sure any keychain or something like that would time out
apparently it needs to store something in the keychain even though I don't understand why... but after ecryptfs-setup-private it told me that it had to do that (it didn't ask me if I wanted or not, it just did)

I'd try your suggestion about reboot in single user mode but the machine is only on the network and I have only a SSH access so that'll be a bit tricky

the machine is only CLI (ubuntu-server if that matters) so no regular keychain nor gnome or even X installed.

this is also not the whole home, it's just the private folder -> and I created it after the install not during the setup... 

maybe I did something wrong while creating it?
I just did a regular ecryptfs-setup-private

I also tried to change the password of the user... sudo could still mount it


is there something like a CLI-based keychain?

---

### Post by amra.sonntag on 2011-01-23
I believe there is a Option in ecryptfs-setup-private, that specifys a Password. You will use this one to mount your folder. By defaul, this option is off.

This password is than stored encrypted and used to decrypt your Private folder. This also means - if you forget it - you will be unable to recover the data inside this Folder.

Obviously this is alot more secure. ;)

Use the --mountpass MOUNTPASS to create your Private folder. In the default setup - this is filled with random numbers.

You can also use --noautomount. I suppose you will have to play around with it for some time.

---

### Post by miticotoby on 2011-01-24
thanks guys for all the help! really appreciate it!


unfortunately the problem is still there. 
root can just always mount my Private folder without any form of password.
I deleted and re-created my private like 1000 times, with MOUTPASS option set without it set (using random pass), with automout set and automout un-set... root can just always mount my Private folder without password....
sudo -u USER ecryptfs-mount-private always works... this is a little frustrating ;/

---

### Post by OpSecShellshock on 2011-01-24
After the folder is mounted by root, can its contents be read in clear text?

---

### Post by miticotoby on 2011-01-24
yes, root can read/write delete whatever in cleartext on the folder

---

### Post by leorolla on 2011-01-24
Wow, I can reproduce it!!!

A security flaw?!

After logging in and out with another user, I could mount/umount his home folder as I wanted, just running "sudo -u USER ecryptfs-mount-private".

Turns out that the keys were not being removed...

So, "sudo -u USER keyctl list @u" was still showing me the keys in the keyring.

Now, after running "sudo -u USER keyctl clear @u", the keys were removed and I couldn't mount /home/USER anymore.

Anyway, I would be surprised if you could do it just after a fresh boot, without logging in as USER.

---

### Post by miticotoby on 2011-01-24
thanks again for all the help on this.

leorolla, yes you were right, a reboot does indeed clear the keyring. after that even when I log in as the user in question using ssh-key-authentication I have to type the actual password -> the way I think it should be (although it'd be nice to be able to use the SSH key as authentication also for the encrypted folder (since it's probably more secure than any password you could ever choose)... anyway that's a different story...

but shouldn't the keyring of a user really be cleared on a logout? this is a serious security issue I think! specially because there is not even a timeout... I tried to wait several hours to the keyring to maybe expire, it just doesn't!
and (like in my case) when the machine in question is a server you can't just reboot it...

for now I made a workaround by putting:

ecryptfs-umount-private
keyctl clear @u

in .bash_logout (you need the umount first otherwise it wont unmount it at all since apperently it needs the key in the keyring to even just unmount the folder)


maybe I gotta figure out on how to submit a bug for ubuntu, what you guys think?


now regarding the key-auth;))
is there a way to get the private-folder-mount going by solely using SSH-key-authentication?

---

### Post by Dave_L on 2011-01-24
This looks like a good place to report a bug, or discuss it further:

[https://launchpad.net/ecryptfs](https://launchpad.net/ecryptfs)

Actually, this existing bug report looks the same: [https://bugs.launchpad.net/ecryptfs/+bug/507150](https://bugs.launchpad.net/ecryptfs/+bug/507150)

---

