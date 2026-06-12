---
title: "What kind of server should I use to access my files through the internet?"
date: 2007-05-27
forum: Server Platforms
---

### Post by Biochem on 2007-05-27
Hi,
I want to be able to access some of my files on my desktop remotely trough the internet and maybe share some of them with a few (less than ten) collaborators. My needs are simple, Read and write capabilities and cross platforms. I'm not scared of people snooping on the files during transfer, however I want to make sure that nobody will be able to erase them from my system (I do have backup but I'd rather not rely on them). 

I've never setup anything more than samba and nfs on my home network so I really don't know where to start. I Googled a bit and this is what I came out with

[LIST]
[*]FTP send user name and password are sent in the clear so it's an unacceptable risk.
[*] My understanding of VPN is that it will open my hole network and often require to install something in windows and is therefore not very practical.
[*] Webdav seems promising but I'm note familiar with it and instruction on how to set it up are intimidating (requires Apache,perl and Mysql).[/LIST]
So my question are:
[LIST=1]
[*]Which one would you recommend and why? Feel free to add any protocol That I'm unaware of.
[*]Could you please suggest some easy to understand howto or manual. After all, I need to start learning somewhere.[/LIST]
Thank you in advance.

---

### Post by Znupi on 2007-05-27
You should try ssh. That's what I use, with the exact same purposes as you.
```
sudo apt-get install openssh-server
```

---

### Post by nix4me on 2007-05-27
ssh and scp.

nix4me

---

### Post by Biochem on 2007-05-27
I admit I didn't think about ssh, I thought it was for remote administration only.

Is it possible to restrict access to a single folder using ss? If I want to share a file with a colleague, I don't necessarily want him to view the whole system tree.

---

### Post by Znupi on 2007-05-27
> **Biochem said:**
> Is it possible to restrict access to a single folder using ss?

As far as I know, that can't be done. I may be corrected.

---

### Post by Frosty Cold Drink on 2007-05-27
> **Znupi said:**
> As far as I know, that can't be done. I may be corrected.

Its possible, but generaly speaking if that type of restriction is required, then SSH isn't the propre choice.


WebDAV+SSL isn't too tought to set up. Neither is FTP+SSL.

---

### Post by ruy_lopez on 2007-05-28
SSH is the ONLY solution. You don't want to share anything else over the internet. Also, use public keys, to authenticate yourself to the ssh server. Otherwise you'll soon be fending off brute force attempts on your password.

---

### Post by craigp84 on 2007-05-28
ruy_lopez - how's the weather where you are?

(What Frosty Cold Drink said)++

---

### Post by ruy_lopez on 2007-05-28
Same as where you are, cause that's where I am, too.

---

### Post by craigp84 on 2007-05-28
> SSH is the ONLY solution

No, you are clearly in cloud cuckoo land.

-c

---

### Post by Styx on 2007-05-30
Why dont try proftp it works for me ist save as fare as i know and it is easy to use

---

### Post by LucasLinard on 2007-07-10
Hi
can I connect to my ubuntu machine via ssh from a windows machine?
If so, what do I need to do?

---

### Post by Frosty Cold Drink on 2007-07-10
> **LucasLinard said:**
> Hi
can I connect to my ubuntu machine via ssh from a windows machine?
If so, what do I need to do?

[LIST=1]
[*]Turn on SSH on your Ubuntu machine.
[*]Get a Windows SSH client.
[*]????
[*]Profit!
[/LIST]

---

### Post by LucasLinard on 2007-07-10
thanks for the quick reply.
I'm really lost around here, Can you point me a good howto to setup thuis ssh server. I've found some howtos but it seems that somwthing is missing.... i'm really lost, It looks like I should know some things that I don't.

---

### Post by piers on 2007-07-11
I would go with fTP + SSL for the sake of easy setup and management from your side, and idiot proof client software.

---

### Post by Biochem on 2007-07-11
All you have to do is install open-ssh
```
sudo apt-get install openssh-server
```
SSH will be installed with basic configuration. The user will be those on the computer with their respective priviledge. But I strongly suggest you have a look here: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
Just so you can secure it a bit. I strongly recommend key authentication.

To access your file you can have a look at [http://winscp.net/](http://winscp.net/) it is very easy to use and can be put on an usb key to make it portable.

If your looking for complete remote access package look for Putty (CLI) and Xming (X forwrding) on Google. again they are portable so they can  used on any computer even without admin privilege.

---

