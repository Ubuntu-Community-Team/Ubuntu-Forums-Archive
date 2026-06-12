---
title: "Ubuntu Server installed, what next? (Just for learning)"
date: 2011-07-18
forum: Server Platforms
---

### Post by sirspazzolot on 2011-07-18
My friend sent me his notes on setting up his home media server so I'll probably try doing that. What other things could I do to learn with Ubuntu Server? I don't intend to make anything for anybody, even me, to use. I just want to get comfortable with this stuff.

---

### Post by papibe on 2011-07-18
Things that I think could be useful:
[LIST]
[*]Enable remote access using ssh (OpenSSH).
[*]Download server (transmission-daemon).
[*]NFS remote folders for backups (nfs-kernel).
[*]SMB remote folders for Windows (samba).
[/LIST]
Just some thoughts,
Regards.

---

### Post by sirspazzolot on 2011-07-18
SSH was the first thing I installed. :D
I'll look into those suggestions tomorrow afternoon. I didn't realize how late it was. What are some fun/useful CLI apps to install? I got Lynx, irssi, and a few others.

---

### Post by donniezazen on 2011-07-18
Subsonic.

I think it is best music server out there.

---

### Post by sirspazzolot on 2011-07-18
Subsonic was actually recommended to me for the home media server. Good to hear more positive feedback on it. Looking forward to using it!

---

### Post by Entilza on 2011-07-18
Install the LAMP Server option if website hosting interests you.  (run tasksel at shell prompt)

Also Webmin would be handy

---

### Post by sirspazzolot on 2011-07-18
[IMG]http://i.imgur.com/ITx8A.png[/IMG]

A picture is worth a thousand words. Nothing there would accomplish what I want, will it? Looks like my options are:[LIST]
[*]forward ports without telling motherdearest since she's convinced that port forwarding is a virus
[*]make her realize that she's keeping me from valuable learning experience because of her reluctance to accept that she's computer-illiterate
[*]get my sister's boyfriend to explain it to her because he's the favorite child
[*]just pay for a damned VPS. reluctant to do this, though, because I'm sixteen and jobless.
[/LIST]

In other news, just got off the phone with comcast. Got us faster internet, and our bill went down $40 less for the next six months, then -$20 after that. Sounds too good to be true though, so I'm a little wary.
[IMG]http://www.speedtest.net/result/1391245555.png[/IMG]

---

### Post by terazen on 2011-07-18
Try playing with virtual servers, lamp, and backup softwares.  I'd do virtual servers first, then you can really do some damage and it is easy to revert back to a backed up (working) image.  If you are trying to learn to get linux or windows certified then you'll want to be familiar with virtual machines for sure.

My original learning box (sparc ultra10 w/solaris) was a firewall, squid proxy, dns, dhcp, and router that I used to learn basic scripting.  For most of that you could use a PfSense virtual machine.

---

### Post by drdos2006 on 2011-07-18
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
### Website is http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

Also This site.
[http://bodhizazen.net/Tutorials/](http://bodhizazen.net/Tutorials/)


regards

---

### Post by kevinthecomputerguy on 2011-07-19
Listen to Dr. Dos
He is wise !!!

---

