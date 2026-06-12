---
title: "Password-less SSH Login doesn't work with Sudo"
date: 2008-12-12
forum: Security
---

### Post by LordKelvan on 2008-12-12
Hi:

I've set-up password-less SSH login for some remote servers.  Everything is now working correctly, except when I try to transfer root-owned files using SCP, because now the command becomes "sudo scp ...".  Now I have to enter the password for my remote account (obviously I have to enter my own local password due to the use of "sudo", which is not a problem) before beginning the transfer.

I remembered that in order to set-up password-less SSH login, I had to add public/private key files to ~/.ssh/, I copied those files to /root/.ssh/.  Afterwards, it wouldn't ask me for the remote account password, but it would ask me for the passphrase for the private key file.  So I started a root shell using "sudo su", ran "exec ssh-agent bash", and then ran "ssh-add /root/.ssh/id_rsa".  However, when I exit out of the root shell, all my identities have been removed (i.e., "ssh-add -l" shows no identities).  Now, if I start a root shell again, and run "ssh-add -l", it also shows no identities.

Can someone tell me the correct way to enable password-less ssh login when transferring root-owned files?

Cheers,
LK

---

### Post by lensman3 on 2008-12-12
I use the following to set up root accounts on my client machines.  I am logged in a text window as root (not using sudo).

After the passwordless key has been generated, I enter:

cat ~/.ssh/id_rsa.pub | ssh user@remotebox "(mkdir .ssh&>/dev/null; chmod 700 .ssh && cat - >> .ssh/authorized_keys )&&chmod 600 .ssh/authorized_keys"

All on one line. Change the "user@remotebox" to the appropriate destination.  It will prompt for the password to run this  script. I copies the local password to the client, sets permissions and exists. I run the script on the server going to the client.  You can run it the other way for uni-directional.

After that as root, I enter "ssh remote" and  I'm instantly logged on in a text window.  If you enter "ssh user@remote", I think you are prompted for a password, especially when "user" is not the same as on the local machine.

Hope this helps.

---

### Post by LordKelvan on 2008-12-13
Thanks for your help, but I think there has been a misunderstanding.  I can get regular password-less login to work (e.g., transferring files, that are not owned by root, from my local computer to a remote computer) - I took the same steps you just mentioned (except I also set-up ssh-add).  

What I can't get working is the following: I have a file, root_owned.txt, that is owned by the root account on my local machine.  I am trying to transfer it to a remote computer, which I have already set-up password-less SSH login, using SCP with the following:
```
sudo scp root_owned.txt remote_user@remote_computer_name
```

Cheers,
LK

---

### Post by The Cog on 2008-12-13
You should be able to copy the file provided your login user has rights to read the file. So fiddling with the file rights might be a solution. Otherwise, all I can think of is to login interactively and copy the file before using SCP, or giving root a password.

---

### Post by koenn on 2008-12-13
> **LordKelvan said:**
> Thanks for your help, but I think there has been a misunderstanding.  I can get regular password-less login to work (e.g., transferring files, that are not owned by root, from my local computer to a remote computer) - I took the same steps you just mentioned (except I also set-up ssh-add).  

What I can't get working is the following: I have a file, root_owned.txt, that is owned by the root account on my local machine.  I am trying to transfer it to a remote computer, which I have already set-up password-less SSH login, using SCP with the following:
```
sudo scp root_owned.txt remote_user@remote_computer_name
```

Cheers,
LK

I think this problem is caused by the fact that, when using sudo to handle the root-owned file, the ssh situation changes from
localuser@here -> remoteuser@there
to
root@here -> remoteuser@there

you've probably set up remoteuser@there to accept passwordless logins from localuser@here, but not (yet) from root@here; you probably need to set up the remoteuser@there account to accept public key authentication from root@here, 
or something, if I understood this correctly.

---

### Post by LordKelvan on 2008-12-14
Yes, if you read my first post, that was also my conclusion.  That is why I copied my public/private key files into /root/.ssh.  My current problem is this:

When I was setting up password-less login, I had to run ssh-add so that it wouldn't ask for the passphrase for my private key (which would have defeated the whole 'password-less' concept).  My problem right now is I cannot get the ssh-add step to work for root, and thus every time I try to do a password-less SCP (which of course uses SSH), it asks for my passphrase.

Can anyone help?

Cheers,
LK

---

### Post by LordKelvan on 2009-01-23
Bump.

---

### Post by Junkhead1984 on 2009-03-09
I am having this exact same issue!  Any help would be greatly appreciated.  I've been scouring forums for hours, but to no avail!

Here is my situation.

I have a laptop, and I have an NX server running on it.  I have a main desktop computer which it reverse connects to, using SSH.  The desktop is then able to monitor the laptop, as long as it has an internet connection.  Not the best anti-theft mechanism, but hey, it's meant more as an academic exercise anyway.

To do this, I have decided to invoke SSH to initiate a reverse forwarding connection to the desktop, whenever the network goes up.  I decided that the easiest way to do this would be to add a script to /etc/network/if-up.d, which would execute SSH as a low level user whenever the network goes up.  Also, I put a corresponding script to shut down SSH in /etc/network/if-down.d, to shut it down whenever the network connection is lost, to avoid any possible conflicts.

All is well and good, I have my SSH systems keyed and everything, requiring no password input whenever I want to initiate the connection.

The only problem is this:  Everything goes down the drain, when sudo is called to execute SSH as a lower level user.

What happens, is that I get prompted to enter the passphrase for the SSH key that I mentioned earlier.  This ONLY happens when sudo is used.  Otherwise?  No problems at all.

I noticed that, when I invoke sudo -i, that the environment variable SSH_AUTH_SOCK is empty, which I believe is the cause of the problem.

Any assistance would be very grateful!  Thank you for your time.

---

### Post by Junkhead1984 on 2009-03-09
Solved it!  Turns out that I was right about SSH_AUTH_SOCK causing a problem!

To solve this, be sure to:

```

exec `ssh-agent` #This sets up the session created by sudo for ssh keying
ssh-add #This adds the necessary keys to connect to the server, passwordless

```

before you call ssh for the forwarding.  Unfortunately, this only works for non-passphrased keys.  If anyone has a better solution, I'd be very interested in hearing it!

---

