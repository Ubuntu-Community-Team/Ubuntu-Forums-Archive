---
title: "Question about SSL"
date: 2009-11-30
forum: Server Platforms
---

### Post by HighCommander540 on 2009-11-30
Hello, Ubuntu forum users! :P

I have a question. I recently installed SSL for Apache and signed my own certificate (I know its not trusted, I am just using the server for me right now). The thing I am wondering about, is the passphrase.

Everytime the server starts the Apache process it requires the passphrase to start the SSL. The problem is I have the server set to start up and shutdown at times it deems so itself. So it won't be able to enter the passphrase itself.  So I was wondering what your opinions are on it? Should I just not use a passphrase? Should I write a Shell script to give it the passphrase as it starts (if so how would I do this, sorry not a master shell scripter)? Or something else?

Also, SSH uses its own key (something with snake in it). Is there anyway I can use that?

---

### Post by BkkBonanza on 2009-11-30
When you create the certificate with openssl it asks for a passphrase. Leave that blank (hit enter) and then no passphrase is attached to the certificate and no prompt is made when it is used. 

I think this is how most people handle it but there may be a more secure way using some kind of preset passphrase. Even so the passphrase would have to be stored somewhere and anyone with root access is going to be able to find it. Leaving a blank passphrase also means anyone with root access to the server can find and use the private key to impersonate (assuming you store the private key with root only permissions, which is what you should do).

I don't believe you can use the ssh key for creating a certificate or to help with the passphrase issue. I don't think you'd want to tie the security of system access together with SSL anyway.

---

### Post by HighCommander540 on 2009-11-30
Yeah, I know you can do that. But it also tells you that its not very safe to do that. There has to be a way otherwise, have the passphrase would be useless. Why would you want to have to type it in everytime the server boots? And how would you...There is no access via terminal or anything how would you enter it at boot-up?

Also, I was wondering how to get it to not force the use of SSL? I have it enabled which I thought meant it would just allow the use of SSL. But everytime I go to access the server it tells me that I can't unless I am using the HTTPS method.

---

### Post by BkkBonanza on 2009-11-30
You need to specify SSL only for the web sites which are listening on port 443. So you would configure a virtual host for normal HTTP on port 80 and a separate one for HTTPS on port 443. They can point to the same or different document roots but access to them is determined by which port the request comes in on. ie. you need to configure two virtual hosts if you want both protocols supported. (Note also that you need a separate IP address for each https domain you serve but it can share that IP for the http one. There are ways to serve more than one https domain on an ip but they are non-standard and not usable by some browsers, making them only useful for private use or testing perhaps)

Using a passphrase-less certificate is not as bad as you would think. Any user who has root access has full ability to compromise the system or replace certificates anyway. That is, if I gain root on your server I can go in and replace certificates with my own. So having root access to use certificates in an automated startup is hardly more compromised than having root access for any other ability to compromise the system. What you don't want is to have certificates usable by non-root users. You need permission 600 for ssl/private keys. Also a user gaining root access is likely going to be able to create new certificates with your ownership spoofed anyway.

The Apache web server will start as root but drops access rights for child threads that service requests.

You are right that it's non-functional to have to enter the passphrase manually when starting Apache and that's why no one does it that way. I did have a look around and found you can automate the passphrase with an apache directive (SSLPassPhraseDialog exec:/path/to/passphrase-file). I just don't see the point in putting your passphrase in cleartext in a file on the server. It's pretty much equivalent to not requiring one unless root. Anyone with root access will easily be able to read the passphrase. This directive also supports piping from a password program, but I believe anyone with root access is likely to be able to likewise force that program to divulge the passphrase. I may be wrong here and would welcome any suggestions where this facility gives real benefit.

---

### Post by HighCommander540 on 2009-12-01
Ok, thanks. I figured that out. I thought turning on SSL just meant that it would give the virtualhost the ability to also transmit over 443. I didn't know that you have to make a new host for the SSL. I did that and it works now.

Thanks for the advice. I see what you mean. It wouldn't make any difference if I ran a script or a program versus a root only access. So I am just going to do that. So I made sure to make it 0600 so only my root can touch it.

Yeah, I know it starts as root, then it moves the processes down to www-data.

Seriously, thanks dude. Now I just need to figure out other stuff to get the server to work how I want it too.

---

