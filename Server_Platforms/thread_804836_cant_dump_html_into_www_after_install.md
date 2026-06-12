---
title: "cant dump html into www after install?"
date: 2008-05-23
forum: Server Platforms
---

### Post by opportunity on 2008-05-23
HI,

i just installed a LAMP server but am unable to dump my website html docs into the /var/www folder as i get permission denied errors. I noticed its owned by root yet im informed enabling the root account is a bad idea for security. What is the proper way to start this off ? some chmod or chown command im assuming?

---

### Post by opportunity on 2008-05-23
sudo chmod 777 /var/www did the trick.

Guess you have to lock it back up like a door after your done writting?

---

### Post by cdenley on 2008-05-23
Anything that requires root access, you use sudo. Some examples.
```

sudo cp index.html /var/www
sudo cp -r my_html/* /var/www
sudo -s
gksudo nautilus

```

---

### Post by kamaji792 on 2008-05-25
The /var/www directory by default is "owned" by root and in the root "group" meaning that pretty much only super-user (root) can do anything.

I think I did the following (assume I have a user "jim"):
```
cd /var
sudo chown jim www
cd www
sudo chown jim index.html
chmod 644 index.html
```

So now jim (and only jim) can modify the files in the www directory and everyone else can read them so Apache will be able to serve them.

The above setup is for a local network facing server.  I have never had the nerve to create one that is open to the Internet.

---

### Post by windependence on 2008-05-25
> **kamaji792 said:**
> The /var/www directory by default is "owned" by root and in the root "group" meaning that pretty much only super-user (root) can do anything.

I think I did the following (assume I have a user "jim"):
```
cd /var
sudo chown jim www
cd www
sudo chown jim index.html
chmod 644 index.html
```

So now jim (and only jim) can modify the files in the www directory and everyone else can read them so Apache will be able to serve them.

The above setup is for a local network facing server.  I have never had the nerve to create one that is open to the Internet.

This is a much more secure way to do it. Having those files world writable on the web is pretty much suicide unless you don't care about being hacked.

-Tim

---

### Post by opportunity on 2008-05-27
any idea what the proper security settings are on www for a Content management system like Mambo?

EDIT : found a good tut on it here:

[http://www.tutorial.hu/letoltes/dl/konyvek/securing_mambo_os-v0.4.pdf](http://www.tutorial.hu/letoltes/dl/konyvek/securing_mambo_os-v0.4.pdf)

---

### Post by NateMan on 2008-05-27
I would never set my www folder to be writable to everyone. The idea of taking ownership and setting it up for your user is a good one. Although using sudo for the file transfer would be good as well. And yes your folder would be destroyed if you ever left it that open.

---

### Post by opportunity on 2008-05-27
> **NateMan said:**
> I would never set my www folder to be writable to everyone. The idea of taking ownership and setting it up for your user is a good one. Although using sudo for the file transfer would be good as well. And yes your folder would be destroyed if you ever left it that open.

How would you go about test hacking your own site? How is modification of content that sits on an apache server possible with only port 80 accessable?

---

### Post by Jonne on 2008-05-27
It might be a problem if you run php/cgi scripts. chmodding it 777 if there's no server-side scripting at all will probably do no harm, but as soon as you have php scripts that have file uploads, you can and will get into trouble.

---

### Post by cdenley on 2008-05-27
> **opportunity said:**
> How would you go about test hacking your own site? How is modification of content that sits on an apache server possible with only port 80 accessable?

It shouldn't be, unless someone finds a new vulnerability in apache or one of your php scripts. Restricting security permissions is just an extra layer of security.

---

### Post by NateMan on 2008-05-27
well what services are running on your server? If you have the permissions set so that anyone or anything can do whatever they want, then a hacker can exploit a service and use service users to do anything rather than root or a specific user. Is it a software firewall only opening up port 80 or a hardware firewall? Anyone could delete those files. There are ways to execute a command such as that and blame no more data. There are a ton of other ways. Just don't do it. Be smart.

---

### Post by NateMan on 2008-05-27
I've always found proper file permissions to be the groundwork for a well running server. Why would you build a house on a bad foundation?

---

### Post by opportunity on 2008-05-27
Its not about the question of weather a solid foundation is a smart idea or not but rather testing that foundation after the fact. Penetration testing?

---

### Post by NateMan on 2008-05-27
Well that is a pretty big gapping hole. I made a few inquires into the subject and found there are a few nasty tricks that your server can be made to do and then if your file permissions are set to allow everyone to read and write, then a person can delete your whole website. I'm not sure how accurate those sources are with todays apache and php, but why not spend a few minutes making it as secure as possible? At least chown it to your normal login user and then set the file permissions back to normal. That way its still secure and you can modify the files. I just upload my files as root to fix the problem, but some people like to just set it to your username. 

Although if your asking for penetration testing... Seriously though do you know anybody trustworthy who could do a good job of it?

---

