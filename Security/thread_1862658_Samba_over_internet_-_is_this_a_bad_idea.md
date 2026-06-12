---
title: "Samba over internet - is this a bad idea?"
date: 2011-10-17
forum: Security
---

### Post by mushy365 on 2011-10-17
I'm going to be going away for a year and i wont have my computer, i thought it would be cool to have a family member turn on the pc in my room running ubuntu and samba  whith a share to all my music. 

So that in a hostel im in, in australia i can set up to connect to my ip and access my music 
now i dont mind who sees the data, i have it set to readonly and no user auth is required. So no passwords will be sent etc. 

I'm just wondering how secure is it to make a share like this available to the internet?

---

### Post by capscrew on 2011-10-17
> **mushy365 said:**
> I'm going to be going away for a year and i wont have my computer, i thought it would be cool to have a family member turn on the pc in my room running ubuntu and samba  whith a share to all my music. 

So that in a hostel im in, in australia i can set up to connect to my ip and access my music 
now i dont mind who sees the data, i have it set to readonly and no user auth is required. So no passwords will be sent etc. 

I'm just wondering how secure is it to make a share like this available to the internet?

Samba is a LAN technology.  It uses broadcasts for NetBIOS resolution.  This means data will not cross your home router to the Internet.  If you want Samba file sharing while traveling you will have to setup a VPN.  This will make your remote computer a member of your home LAN.

Look at information on OpenVPN for a solution.

---

### Post by bodhi.zazen on 2011-10-17
Samba over the internet is indeed a bad idea. Look into any number of alternates from ssh (scp) to http (one way) to torrents to rsync.

---

### Post by a2j on 2011-10-17
vpn or sftp

---

### Post by papibe on 2011-10-18
I think you would be better off using a service like [Dropbox]("http://www.dropbox.com/"), or [Ubuntu One]("https://one.ubuntu.com/"). Also [Google Music]("http://music.google.com/about/") seems to be designed to do just that.

Regards.

---

### Post by dirtrider1 on 2011-10-18
There is basically two routes you can take, the first is to setup your own server and the second is to host your data.

If you wan't to use your own machine running Ubuntu Samba alone will not cut it over the Internet, I recommend looking into ssh and the various way's its used like sftp and sshfs because if set up correctly it is highly secure and easy to set up. A more complex method but equally secure would be setting up a vpn ideally Openvpn and running Samba or any other file transferring protocol over it. The vpn method would probably be preferable over ssh for a permanent set up. I would not use the family pc for this task for a variety of reasons, get an old pc and use it as a stand alone server and install Ubuntu Server and leave it powered on or look into something like linode.com which is a virtual private server with root access.

---

### Post by clblanchard on 2011-10-18
These are all really good ideas, but if you just want to access your music I would definitely look into ampache :guitar:.  I use it to stream music to my work PC and also around the house.  It's a little tricky to set up the first time, but after that it's cake. 

Cheers!

---

