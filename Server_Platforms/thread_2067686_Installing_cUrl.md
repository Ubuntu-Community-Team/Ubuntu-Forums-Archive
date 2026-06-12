---
title: "Installing cUrl"
date: 2012-10-07
forum: Server Platforms
---

### Post by brandonBuster on 2012-10-07
I don't have much experience installing packages on a live server.

I'm trying to install cURL. I've already got the full LAMP stack installed, but when I try to install cURL I receive a notice saying other packages will be installed:
libapache2-mod.php5
php5-cli
php5-common
php5-d
php5-mysql

I know the server already has some of these packages installed. Will these new installations override my existing packages? If so, could this corrupt my configs?

Thanks!

---

### Post by hydn79 on 2012-10-07
I'm not on Ubuntu anymore but. Yes, most likely. 

Are you doing?:
apt-get install php-curl

or 

apt-get install php5-curl

How did you install PHP? What package?

I always compile from source for best control. Eg:
./configure --enable-fpm --enable-session --enable-xml --enable-libxml --with-mysqli --with-zlib --with-bz2 --with-curl --with-gd --with-openssl

---

### Post by brandonBuster on 2012-10-07
I attempted install with apt-get install php5-curl.

Sorry I can't answer your second question. I'm not sure how all the LAMP packages were installed, as I didn't do them myself.

To compile from source, I found this [article]("http://thermo.sdsu.edu/testhome/phpinstall.html"), steps 12-16.

Would this be your suggestion?

Thank you for your prompt initial reply.

---

### Post by Lars Noodén on 2012-10-07
curl doesn't have those dependencies you mention.  Those must be coming from some other source.  AFAIK installing them will not overwrite existing configuration files, but they are not needed for curl itself.

---

### Post by hydn79 on 2012-10-07
Yes follow steps 12 to 16. Then after "make install" you just have to add curl to php.ini

example:
extension="curl.so"

---

### Post by brandonBuster on 2012-10-07
@Lars, yes I was confused why I as told to add these unrelated packages. cURL is the first thing I've tried installing since running apt-get update this morning. Could this be Ubuntu's way of telling me to update those packages?

@Hydn thanks again for your help. I'm still a little skittish when it comes to CLI so compiling things manually makes me nervous. But these instructions look simple enough. Ill do some more reasearch why apt-get is asking for these things. If I can't find an answer I'll do the manual compile this evening

---

### Post by Lars Noodén on 2012-10-07
It depends on what the text is that precedes the list of packages.  You can update the system with upgrade.

```

sudo apt-get update
sudo apt-get upgrade

```

---

