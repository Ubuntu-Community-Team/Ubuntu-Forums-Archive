---
title: "Remote Login Not Recognizing SSO Credentials"
date: 2013-09-30
forum: Ubuntu One (CLOSED)
---

### Post by nathan14 on 2013-09-30
**Details:**

_OS*:*_  Ubuntu 13.04
_OS TYPE_:  64-bit

TechNCC@Gatormation:~# uname -a
Linux Gatormation 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

**Problem:**

Quite simply, I went to [https://uccs.landscape.canonical.com/edit/](https://uccs.landscape.canonical.com/edit/) and set up the necessary RDP credentials for remote-login.  I have read online that from here, I should be able to visit the unity-greeter login screen, click Remote Login, type in my SSO credentials ( same as Ubuntu One, email + password ), and it take me to another login screen with all of the the RDP 'accounts' I have created.

The problem is that it does not recognize my credentials.  I login with the exact credentials I use for Ubuntu One and, again, it says that my email/password is invalid.  Am I missing something?

( *The reason I posted in the Ubuntu One forum is due to it using my SSO as the remote-login credentials. I apologize if I missed a more suitable forum. *)

---

### Post by TheFu on 2013-10-01
Uh ... I must be missing something.  In my world, where we do not trust 3rd parties any more than absolutely necessary, Canonical has ZERO to do with authentication and logins.

I've never used Landscape.
I've never used Ubuntu One.

Remote access to my systems can happen in a few different ways. Each is based on ssh and ssh-keys. We do not allow password-based remote logins here; too easy to be compromised.  Also, Ubuntu doesn't use RDP natively for remote access to my knowledge.  VNC and ssh are the most popular methods by far ... with VNC requiring a VPN or ssh-tunnel if you care about any security at all.  I use NX for remote desktops and ssh for shell/CLI access.  Ssh is used 98% of the time.

Do you need a GUI?
So, [this]("http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop") is a little dated, but I still think those tools will work.

If not, using ssh is 
a) more secure
b) less bandwidth
c) easier to automate
[Here's how to setup remote access]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") via ssh.

Found this for [setting up VNC through SSH]("http://askubuntu.com/questions/304017/how-to-set-up-remote-desktop-through-ssh"). It is probably what you want.

Don't forget that remote access outside the firewall means you'll need to open ports and secure the inbound traffic in some way.  [Tips to secure ssh connections]("http://www.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures") will help.

---

### Post by stephencweston on 2013-10-04
Hi Nathan,

I highlighted this issue as a bug not longer after 13.04 was released. Unfortunately the feature still seems to be an issue. [https://bugs.launchpad.net/bugs/1181772](https://bugs.launchpad.net/bugs/1181772)

There is another package that is required for it to work that isn't installed by default (in a terminal try 'sudo apt-get install python3-pycurl' to install it). I found this got me past the greeter's remote login feature not recognising my SSO credentials.

Now I get the list of RDP accounts I've set up, but none of them seem to connect. Again it seems to have an issue with my username or password details.

It's a big shame that this feature seems to have been neglected, especially as it was a big part of the 12.10 release. I found it incredibly useful, but haven't been able to get it to work since I upgraded from 12.10.

Please let me know your experience once you've tried the suggestion above.

Stephen

---

