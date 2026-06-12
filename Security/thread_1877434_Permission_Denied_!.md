---
title: "Permission Denied !"
date: 2011-11-08
forum: Security
---

### Post by s.hijazi on 2011-11-08
Hello everyone,
thank you for the ubuntu forms :)
i'm trying to do a project in my course Networking Administration , my project is about to create HTTPS, i use Ubuntu 11.04 and i install it using VMWare ,(my base OS is Windows 7 Ultimate)
i install the apache2 , by this command```
sudo apt-get install apache2 
```

and now i'm trying to create my ssl :
```
mkdir /etc/apache2/myssl 
``` and it said to me permission  denied ! 

how can i solve this problem ? 
thank you :)

---

### Post by matt_symes on 2011-11-08
Hi

Try
```

sudo mkdir /etc/apache2/myssl
```Anything that changes the system folders - as opposed to your home folder - requires elevated privileges so use sudo.

Kind regards

---

### Post by s.hijazi on 2011-11-08
Thank you this work :)
i have another problem now :
i try this code 
```
 open ssl req -new > server.cert.csr
```

and error is : ```
bash: server.cert.csr: Permission denied
```

how to enable all permission ?

---

### Post by matt_symes on 2011-11-08
Hi

If you are doing a lot of work that requires elevated privileges you may find it easier to use a root terminal or console.

To enter the root terminal.

```
sudo -i
```Type your commands. When you have finished type

```
exit
```This will take you back.

It goes without saying, be very careful in the root terminal and exit it as soon as you can. Remember you can do anything to your system.

Kind regards

---

### Post by lisati on 2011-11-08
As matt_symes says, care is needed with elevating privileges. More information about the "sudo" approach can be found at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by matt_symes on 2011-11-08
Hi

That is an excellent article that Lisati just posted and you are highly recommended to read it.

Understanding sudo is a cornerstone of Ubuntu.

This is one way to run your command using sudo

```
sudo bash -c "open ssl req -new > server.cert.csr"
```You are getting the 'permission denied' error due to the redirection to the system file.

Kind regards

---

### Post by s.hijazi on 2011-11-08
[FONT=Comic Sans MS][SIZE=2][COLOR=Black]Thank you :)

now i'm here 
/etc/apache2/myssl$ 

```
openssl rsa -in privkey.pem -out server.cert.key
```
after demand of password , and write it , 

error :
```

unable to load Private Key
2110:error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:evp_enc.c:330:
2110:error:0906A065:PEM routines:PEM_do_header:bad decrypt:pem_lib.c:428:

```

what's the error and how to solve it ? [/COLOR][/SIZE][/FONT]

---

### Post by matt_symes on 2011-11-08
Hi

It's having trouble decrypting the key by the looks of the error message.

Can you post a link to the tutorial you are following ?

I have never set up an SSL certificate so i may not be the best help here.

Kind regards

---

### Post by s.hijazi on 2011-11-08
[FONT=Comic Sans MS][SIZE=2][COLOR=Black]Hello .
Dear Mr "matt_symes" 
my tutorial is :
[http://www.youtube.com/watch?v=DCv3obo--OM](http://www.youtube.com/watch?v=DCv3obo--OM) 

i don't understand Germany-Language but i follow the command in the terminal.
first before begin in command on this tutorial you may install apache2
[/COLOR][/SIZE][/FONT]```
sudo apt-get install apache2
```

Thank you for any idea can help me :) 

[FONT=Comic Sans MS][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][/FONT]

---

### Post by matt_symes on 2011-11-08
Hi

I have apache on my server and i will have a play for you later.

You don't speak German ? No wonder you are having problems ;)

 Did you enter the correct passphrase at this step?

```

openssl rsa -in privkey.pem -out server.cert.key
```

Kind regards

---

### Post by s.hijazi on 2011-11-08
yes i enter the correct password :)

---

### Post by emiller12345 on 2011-11-08
FYI:  I know it sounds like your trying to put this together by hand for learning purposes, but Ubuntu has a very simple command for installing Apache + MySQL + PHP all in one shot.For those wanting to have it all set up for them...```
sudo tasksel install lamp-server
```However, I have not found a way to undo this easily, so you my want to try it out in a virtual environment first to make sure its what you want...

---

### Post by matt_symes on 2011-11-08
Hi

Have a read of this as my German ist nicht sehr gut.

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

It's for Ubuntu and it's newish.

@emiller12345

I think the OP is trying to create a SSL self certificate. That's what the video is about. I think he already has a LAMP stack set up.

Kind regards

---

### Post by emiller12345 on 2011-11-08
Ah. I was writing faster then my eyes could read. sorry.
I do know that openssl has a bunch of helper scripts in the downloadable source files.
```
$ cd ./openssl-1.0.0e/apps
$ perl CA.pl --
usage: CA -newcert|-newreq|-newreq-nodes|-newca|-sign|-verify
$ perl CA.pl -newcert
```
can help in making a cert without needing to mess with the config file.

---

### Post by s.hijazi on 2011-11-09
Thank you Every one :) my prob is solved :)

---

