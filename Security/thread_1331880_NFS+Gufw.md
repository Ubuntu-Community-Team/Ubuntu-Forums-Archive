---
title: "NFS+Gufw"
date: 2009-11-19
forum: Security
---

### Post by jessiebrownjr on 2009-11-19
I installed NFS, was reading about its insecurities. I don't know alot about it yet but I have my hosts.deny set to ALL : ALL and my hosts.allow set to my local range of IPs for my client PCs. Did a port scan and it showed I had 111 up and something else. 

I installed GUFW after and put it on block all incoming traffic. Is this enough to be secure?

I haven't tried to mount the server yet because I have been busy but just theorycrafting for a bit to make sure what im doing is right.

---

### Post by bodhi.zazen on 2009-11-19
If you block all incoming traffic you will not be allow to connect to yoru nfs server.

Open a terminal and enter either :

```
sudo ufw allow nfs
```

This will allow all nfs traffic, so restrict ip with /etc/hosts.deny and /etc/hosts.deny

Or ...

```
sudo ufw allow from 192.168.0.0/24
```

This will allow all connections from you LAN. Again you can restrice with /etc/hosts.allow /etc/hosts.deny.

If you want to be more precise in your use your firewall, you will need to look up the nfs ports and allow those ports , either with ufw or iptables.

---

### Post by jessiebrownjr on 2009-11-19
I think the local rule is my cup of tea, if I'm worried about bad NFS juju I don't want to let it past the firewall hehe, thanks!

---

### Post by movieman on 2009-11-19
Does UFW actually handle the NFS server ports changing every time you reboot?

---

### Post by bodhi.zazen on 2009-11-20
> **movieman said:**
> Does UFW actually handle the NFS server ports changing every time you reboot?

I don't know, it appears it will, but I have not tested it.

Personally, I use iptables and samba (IMO samba is more secure then nfs :popcorn: )

---

### Post by jessiebrownjr on 2009-11-20
> **bodhi.zazen said:**
> I don't know, it appears it will, but I have not tested it.

Personally, I use iptables and samba (IMO samba is more secure then nfs :popcorn: )
Interesting hehe

Might I ask how it is insecure if I have it only allowing local connections? im 100% insecure if somebody hacks my WPA2 at my house but other then THAT... lol

Serious question too lol

---

### Post by movieman on 2009-11-20
> **bodhi.zazen said:**
> Personally, I use iptables and samba (IMO samba is more secure then nfs :popcorn: )

I gave up on Samba because it's slow, unreliable and poorly integrated with Linux: for example, Firefox can't open a file that's on a Samba server whereas it will happily read from NFS.

I believe both use Kerberos these days if you have that configured, so security-wise it should just come down to who has the most bugs. I use IPSEC and IP-based firewalls on the NFS server so there's no risk of someone mounting NFS drives without permission.... but I did have to find the right configuration options to change to get it to use fixed ports, and change all the user IDs so they match on different machines.

---

### Post by bodhi.zazen on 2009-11-20
> **jessiebrownjr said:**
> Interesting hehe

Might I ask how it is insecure if I have it only allowing local connections? im 100% insecure if somebody hacks my WPA2 at my house but other then THAT... lol

Serious question too lol

You should be fine if you are behind a firewall. But yes, if someone cracks your LAN NFS is wide open.

> **movieman said:**
> I gave up on Samba because it's slow, unreliable and poorly integrated with Linux: for example, Firefox can't open a file that's on a Samba server whereas it will happily read from NFS.

I will grant you NFS is faster then Samba. However I have to disagree with the rest of your observations.

I would not consider Samba to be unreliable or poorly integrated with Linux.

Just so we do not confuse Samba with Microsoft products :

Samba is [Free     Software]("http://www.gnu.org/philosophy/free-sw.html") licensed under the [GNU     General Public License]("http://www.samba.org/samba/docs/GPL.html"), 

In terms of not being able to open a file on a Samba server with firefox, that is just outright wrong. Frankly it sounds as if you did not configure your samba server properly or you did not have permissions.

> I believe both use Kerberos these days if you have that configured, so security-wise it should just come down to who has the most bugs. I use IPSEC and IP-based firewalls on the NFS server so there's no risk of someone mounting NFS drives without permission.... but I did have to find the right configuration options to change to get it to use fixed ports, and change all the user IDs so they match on different machines.

Your configuration is not exactly out of the box NFS. The NFS server alone, out of the box, as a stand alone server, is less secure then a stand alone, out of the box samba server.

Of course both can be further hardened.

---

### Post by movieman on 2009-11-20
> **bodhi.zazen said:**
> I would not consider Samba to be unreliable or poorly integrated with Linux.

Well, at work I run CentOS and it routinely disconnects from the shared network systems (I'm not sure whether the servers are Windows or Samba on Linux) and requires me to reboot the machine before I can connect again. That's an older kernel, but something there is fundamentally unreliable.

My netbook also can't connect to the Ubuntu Samba server, but I suspect that's a Windows issue rather than Linux (the XP Pro machines connect fine, but the XP Home doesn't). Either way, it's a long way from 'just works'.

> In terms of not being able to open a file on a Samba server with firefox, that is just outright wrong.

So how do you do it? That was the thing that finally pushed me into switching to NFS, because my girlfriend kept complaining that she couldn't email pictures from the file server to her friends.

I go to 'Open File' in Firefox and there's no option anywhere to pick a file off the network. From what I remember even Samba bookmarks don't work.

If you can solve that, I might reconsider Samba, though now I've got the automounter and firewall working there's not much reason to change back from NFS.

> Frankly it sounds as if you did not configure your samba server properly or you did not have permissions.

We can open the files fine from the file browser, but not from most other applications. Generally there's either no way to select a file on a network share, or it rejects an smb: path if it lets you type the path rather than select from the GUI.

Now, that said, the NFS automounter has a similar problem as you can't select a directory which hasn't been mounted yet. That's a fundamental flaw in the Linux GUIs.

> Your configuration is not exactly out of the box NFS. The NFS server alone, out of the box, as a stand alone server, is less secure then a stand alone, out of the box samba server.

Probably... but anyone who takes NFS seriously will likely be using Kerberos and then it's at least as secure as Samba.

---

### Post by bodhi.zazen on 2009-11-21
In firefox go to File -> open file -> in the next window navigate to the samba share -> click open

In terms of your Centos server, OUCH, that does sound problematic. I have not seen that with Centos (I am familiar with centos) but I would not consider that experience typical of Samba.

There is nothing wrong with the way you have set up NFS, in fact it is rather sophisticated. Just do not take your experience with Samba as typical of samba.

---

### Post by movieman on 2009-11-21
> **bodhi.zazen said:**
> In firefox go to File -> open file -> in the next window navigate to the samba share -> click open

But how do you do that?

In the file browser there's a 'Network' icon on the left side where you can go to Samba shares, but in Firefox that icon isn't there. I don't think it's there in any other applications that I use regularly either.

Thinking about it last night, we could presumably automount Samba shares like NFS, but I'm guessing that would lose the user permission information and require putting passwords in /etc/fstab.

---

### Post by bodhi.zazen on 2009-12-04
Sorry for the late responxe, but I lost track of this thread.

Firefox will not mount the samba share. You can mount the samba share in many ways including an entry in fstab if you wish. When using fstab, use a credentials file that is ro by root ;)

---

