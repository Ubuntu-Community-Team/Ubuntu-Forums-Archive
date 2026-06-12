---
title: "ftp users w/shell"
date: 2006-03-15
forum: Server Platforms
---

### Post by johnnyis42 on 2006-03-15
i'll spare everyone the details and make this as simple as possible.

using vsftp for ftp accesss on ubuntu 5.10 configured with no anonymous access, chroot jail to home directory for local accounts.

there is only one account i am concerned about that i will be using in lieu of anonymous access for folks i need to get files to as quickly and painlessly as possible.  my only concern is that in order to get the above configuration to work, i had to give the unprivilidged ftp user accounts i created an actual shell (they would not authenticate if their shell was set to /bin/false or /dev/null).

i did deny access to these accounts in ssh, but i'm curious as to what risks i would face were someone to get ahold of the username and password from the human element i had previously given access to.

my strategy as of now is that the account is chroot in their home directory jail with no files (not even the .profile or .whatevershell files) and only r-x access to the home directoy, and is explicitly denied login to ssh.  so, i'm assuming they can't upload anything through ftp, and thus can't execute anything that could elevate their access in some way.

assume is the operative term here.... am i missing something in the way of another vector to gain unwanted access with this account?  besides specific openSSH vulnerabilities that may come along, am i putting too much faith in the chroot jail vsftp impliments?

all suggestions and beratement of my security ignorance is welcome,

---

### Post by colo on 2006-03-15
I don't know how Ubuntu ships its PAM-configuration, however, /bin/true (and any other executeable) should most probably work as a login-shell when listed in /etc/shells. So you'd just have to add your "shell" of choice (I suggest /bin/true, so it's possible to make a distinction between folks who are just trying to log in, and those who KNOW THE PASSWORD for the account, and try to log in as well) to that file, set the anonymous user's shell to that executeable, and you'd be set.

There's an excellent anonymous-read-only-ftpd, by the way, called oftpd. I'd recommend oftpd for anonymous access, and the sftp-subsystem of openssh2 for actual users of your system. ftp is inherently insecure due to clear-text password- and data-transmission; sftp strongly encrypts both.

---

### Post by johnnyis42 on 2006-03-15
ok, that clears some things up.  let me just make sure i'm understanding this:

/bin/false is an executeable file used as a shell used to dissalow local login to an account, and /bin/true is the same but it does allow login, with no actual shell access persay.

in which case setting a user account's shell to /bin/true allows them to password authenticate, without the ability to execute anything within a shell that has any interaction with the kernel.  yes? no?

---

### Post by johnnyis42 on 2006-03-15
ok, regardless of what i said above, right or wrong, using /bin/true as the shell yields the same result as /bin/false in that the account will not authenticate.

any other suggestions or points?  i still have to use some actual shell to succesffully login using vsftpd as the ftp server.

i'm trying to find all the possible options to deny login access to any interface without restricting ftp authenticaiton with the account.  if this the wrong way to go about this type of lock down?

presently i'm simply restricting access to ftp from the firewall until i can find a good solution and just leave it open that point on.

thx in advance.

---

