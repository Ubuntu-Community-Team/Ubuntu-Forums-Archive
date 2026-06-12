---
title: "ssl and apache"
date: 2007-04-10
forum: Server Platforms
---

### Post by maxwas on 2007-04-10
Hello all,

I have a test box with ubuntu server with xubuntu-desktop running locally on my lan. I have been using the box for playing around with apache2. I have managed to get it up and running no probs with php, mysql, virtual hosts, userdirs, and ssi.

I would now like to have a shot at ssl but do not really know where to start. There is an ssl folder in /etc/apache2 but it is empty :confused: 

Can anyone point me to a nice beginners tutorial. I have used all the tutorials on this forum to get me to the point i am now at, they have been great, so im sure there must be one somewhere :)

Thx in advance

Max

---

### Post by heimo on 2007-04-10
Try this one:
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

---

### Post by maxwas on 2007-04-10
Fantastic!!

Thanks very much

:)

---

### Post by maxwas on 2007-04-10
Ok, i used the guide and it worked a treat - this was done on a box running ubuntu server with a default LAMP install. Only one minor difficulty, when i open up the browser running on the box and:
> [https://localhost](https://localhost) 
it works fine.

Now when i go to another box on the lan and try:
> https://<server_ip>
apache returns an unexpected error (and code), is there any way to get around this?

Another problem i have is i have ubuntu 6.10 running on another machine under vmware. I have LAMP installed on this as well, but it was installed using this command:
> sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 php5-mysql libapache2-mod-php5 libapache2-mod-auth-mysql 
when i try to follow the ssl howto, the command:
> apache2-ssl-certificate -days 365
will not work is there perhaps something i missed in my install?

Many thx

Max

---

### Post by darrenm on 2007-04-10
Ref problem 2. Does it say apache2-ssl-certificate not found?

Seems to be missing from the current build package.

---

### Post by maxwas on 2007-04-10
yep,

> bash: apache2-ssl-certificate: command not found


I have tried comparing the ubuntu server install with the manual install and all the same stuff seems to be there.

Thx

---

### Post by darrenm on 2007-04-10
Theres a bug report for Feisty [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/77675](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/77675) so Im not sure why its happening on Edgy.

---

### Post by MadeR on 2007-04-20
quick workaround taken from debian bug tracker: 

sudo mkdir /etc/apache2/ssl
sudo /usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem

---

### Post by llamakc on 2007-04-23
I tried the Debian workaround and had no luck with it.

---

### Post by MadeR on 2007-04-23
did you install the ssl-cert package?

sudo apt-get install ssl-cert

---

### Post by llamakc on 2007-04-23
Yeah, all is installed. I get the same nebulous error as maxwas does.

---

### Post by llamakc on 2007-04-23
My bad. I forgot to symlink /etc/apache2/sites-available/ssl to sites-enabled/ssl. All fixed.

---

### Post by maxwas on 2007-04-27
It turns out that the same bug now exists in the new server 7.04 as well, whereas in the previous server ver it took the command fine. If you installed LAMP manually on 6.06 desktop the command worked also.

Personally i think for a server distro this needs to be working. For ubuntu to not have addressed this problem, its pretty bad :(

I will try this workaround and see how it goes.

Thanks all

---

### Post by maxwas on 2007-04-28
> **maxwas said:**
> It turns out that the same bug now exists in the new server 7.04 as well, whereas in the previous server ver it took the command fine. If you installed LAMP manually on 6.06 desktop the command worked also.

Personally i think for a server distro this needs to be working. For ubuntu to not have addressed this problem, its pretty bad :(

I will try this workaround and see how it goes.

Thanks all

And it worked fine! :-P 

Big thanks to MadeR and llamakc, you saved me a *ton* of hassle.

---

### Post by MadeR on 2007-04-28
you're welcome!

---

### Post by Shane N on 2007-09-06
> **MadeR said:**
> quick workaround taken from debian bug tracker: 

sudo mkdir /etc/apache2/ssl
sudo /usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem

Building on this, if you add the following line to $HOME/.profile, you'll be able to simply run apache2-ssl-certificate as if it were installed (you'll need to log out/in to make it work the first time):
> alias apache2-ssl-certificate='sudo /usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem'

---

### Post by mathieubill on 2007-09-10
> **Shane N said:**
> Building on this, if you add the following line to $HOME/.profile, you'll be able to simply run apache2-ssl-certificate as if it were installed (you'll need to log out/in to make it work the first time):

Except that this command issues a certificate valid for only one month.
In the original script apache2-ssl-certificate, you could pass a -days xxx as an argument. With the debian script, you can't. I am currently looking for a solution for this.

---

### Post by nowhere@cox.net on 2008-01-02
Has anyone modified the debian script yet to allow passing the number of days? 

Thanks,
Eric

---

### Post by MJN on 2008-01-03
I recommend jsut rolling your own e.g. [http://www.modssl.org/docs/2.8/ssl_faq.html#ToC28](http://www.modssl.org/docs/2.8/ssl_faq.html#ToC28) as it's always useful to know and understand what's going on 'under the hood' so to speak.
 
Alternatively, see mlind's suggestion of extracting ssleay.cnf and apache2-sll-certificate from Edgy's package - [https://launchpad.net/ubuntu/+source/apache2/+bug/77675/comments/15](https://launchpad.net/ubuntu/+source/apache2/+bug/77675/comments/15)
 
Mathew

---

### Post by Nimefurahi on 2008-01-17
Eric (nowhere@cox.net) had asked about a mod to the Debian make-ssl-cert script to extend its longevity.

Here's a 'dirty' mod to /usr/sbin/make-ssl-cert  to accomplish just that:

Line 118 of the make-ssl-cert script reads:```
openssl req -config $TMPFILE -new -x509 -nodes -out $output -keyout $output > /dev/null 2>&1
```

Simply edit this line to read:```
openssl req -config $TMPFILE -new -x509 -nodes -out $output -keyout $output **-days 3650** > /dev/null 2>&1
```

Notice the inclusion of > **-days 3650** That will give your certificate a 10 year life span. And be assured, Ubuntu will still be here in 10 years!

After saving the edited /usr/sbin/make-ssl-cert, simply run it again:
```
sudo /usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
```

Peace!

---

### Post by wally83 on 2008-02-15
Thanks, Nimefurahi! That solved my (as well as other Gutsy users) problems.

---

