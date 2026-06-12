---
title: "Concern: I can see multiple configured Windows networks..."
date: 2004-11-09
forum: Server Platforms
---

### Post by HiddenWolf on 2004-11-09
Hi,

This is probably an unusual situation, but here it goes.
I am in a student building, where internet is offered by the university.
There is a massive 100mbit network for all (250ish) occupants.

While checking the network in nautilus, to my amazement I could see dozens of Windows-networks.
I have not been able to, or tried beyond clicking a few of them, to acces any.

However, I want to make sure that none of them can acces my pc.
Now I have never done anything with Linux security, so I have no clue if I am vunerable, in which way, why, and most importantly how to solve it.

Can anyone offer me tips, suggestions or tell me what to google for?

Thanks,

---

### Post by jdong on 2004-11-09
Samba isn't installed by default on Ubuntu; only the smbclient is. You can see other SMB/CIFS systems, but others can't see you, because you don't have the filesharing server running.

Even if you installed samba via APT or Synaptic, by default NO USERS are enabled, and all shares are password protected by their owners.

Even if you use smbpasswd -a <username> to enable Samba logins with your username, others still need a password to access \\yourmachine\yourusername.

In otherwords, there's multiple layers of security!

---

### Post by HiddenWolf on 2004-11-10
So I need not worry?

---

### Post by jwenting on 2004-11-10
[QUOTE=HiddenWolf]So I need not worry?[/QUOTE]
 No, no need to worry.
At the moment the situation is similar to having a Windows machine with no shares installed, noone can access your machine (though they may be able to see that it's there).

If you install Samba and activate it it's like having a Windows machine with password protected shares, only people with the correct password can access them.

---

### Post by Razvan on 2004-11-10
[QUOTE=jwenting]
At the moment the situation is similar to having a Windows machine with no shares installed, noone can access your machine (though they may be able to see that it's there).

[...] only people with the correct password can access them.[/QUOTE]


well...theoretically...in windowses else than xp/200 its fairly easy and in xp/2000 just a bit harder :-)

---

### Post by HiddenWolf on 2004-11-10
Obviously I run ubuntu at the moment.

I don't mind all those networks, but I want to be 100% sure I am secure.

---

### Post by wasabi on 2004-11-10
[QUOTE=jwenting]No, no need to worry.
At the moment the situation is similar to having a Windows machine with no shares installed, noone can access your machine (though they may be able to see that it's there).

If you install Samba and activate it it's like having a Windows machine with password protected shares, only people with the correct password can access them.[/QUOTE]

Not exactly. Running Windows is like having Samba installed but with shares such as C$ and IPC$ set up. All the time. There is no way to disable these shares other than a firewall. These shares, and all the other RPC endpoints in Windows are open 24/7. The important ones are password protected.

Running Linux without Samba installed is to completely remove this entire critical subsystem of WIndows. There will be no ports open for these services.

Although these shares and services on Windows are password protected (Just like if you installed Samba), they are open services. That means a remote computer can connect and TRY to get in. In the event that there is a vulnerbility that doesn't require a password (like most of the recent RPC vulnerbilities with Windows) your system is wide open to those who know how to exploit it.

Rule of thumb: It's better to not have something installed than to have it installed and not use it, because somebody else might. ;)

---

### Post by HiddenWolf on 2004-11-11
My concern is my ubuntu system.

Is there anything at all installed by default that would allow any of these windows pc's to get onto my pc in any possible way?

---

### Post by allen on 2004-11-11
[QUOTE=HiddenWolf]My concern is my ubuntu system.

Is there anything at all installed by default that would allow any of these windows pc's to get onto my pc in any possible way?[/QUOTE]
 no.

---

### Post by HiddenWolf on 2004-11-11
Thanks.

Now I will resist my childish urges and refrain from asking for tips on how to go and find out if any of these other pc's has anything interesting on it. :-)

*chuckle*

---

