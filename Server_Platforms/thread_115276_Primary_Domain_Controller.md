---
title: "Primary Domain Controller"
date: 2006-01-10
forum: Server Platforms
---

### Post by Cubicegg on 2006-01-10
Hi 

I am very new to linux and after having tried other flavors have decided to stick with Ubuntu. 

I am hoping to setup the machine running Ubuntu as a primary domain controller and for 2 XP clients to connect to the server.

Please would somebody help me out and offer a step by step guide as to what to do, as I'm a little stuck after having read several samba and ubuntu confi guides. I also understand that I should be able to run Swat, however, alas I can not :( 

Many thanks
James

---

### Post by LordHunter317 on 2006-01-10
I wouldn't bother with SWAT, it generates poor configurations.

Have you looked at the offical Samba HOWTO on samba.org?  It has a whole chapter dedicated to just this.  If read and don't understand it, please post specific questions and your configuration.

---

### Post by kejar31 on 2006-01-10
You can just simplify the whole thing by just downloading the script by Matt Oquist on this site. It is made for ubuntu as well. It will setup a samba3 PDC/Ldap server with roaming profiles and home directories in about 10 min.
The download comes with a how-to as well.

[http://majen.net/smbldap/](http://majen.net/smbldap/)

---

### Post by Cubicegg on 2006-01-10
hi

I have played with the script and I cant get it to work either .... what would be real handy is if there was step by step clear instructions on how to get either the script or just using samba to work, perhaps a video tuturial?

thanks

---

### Post by kejar31 on 2006-01-10
[QUOTE=Cubicegg]hi

I have played with the script and I cant get it to work either .... what would be real handy is if there was step by step clear instructions on how to get either the script or just using samba to work, perhaps a video tuturial?

thanks[/QUOTE]

A video tutorial? LOL :D. Maybe someone else can install and setup samba for you. That way you don't have to learn anything at all.:rolleyes: 

Sorry if I sound blunt, but a lot of use on these and other forms spend a lot of time reading and reading and reading on projects like samba. We test it on systems and we get our selves to the point where we just feel comfortable with the software. Some people like to take the easy way out on that, and that's ok. But instead of asking for a video tutorial maybe you should explain what went wrong with the script.

---

### Post by Cubicegg on 2006-01-10
hi 

no you dont sound blunt. a video tutorial would be easier, and to be fair if i get this working will maybe do one myself.

to start with the script refers to ./smbldap.pl which doesnt work instead you need to run ./smbldap-install however this works but does it? it does nt do what it is suppose to do, instead, only askes what linux distribution you are using and then comes to the green text that says "This script has appended its output....." 

if this is correct, please forgive me.... what shall i do next though??? 

thanks James

---

### Post by kejar31 on 2006-01-10
[QUOTE=Cubicegg]hi 

no you dont sound blunt. a video tutorial would be easier, and to be fair if i get this working will maybe do one myself.

to start with the script refers to ./smbldap.pl which doesnt work instead you need to run ./smbldap-install however this works but does it? it does nt do what it is suppose to do, instead, only askes what linux distribution you are using and then comes to the green text that says "This script has appended its output....." 

if this is correct, please forgive me.... what shall i do next though??? 

thanks James[/QUOTE]

Yes I do remeber, you are correct you must type ./smbldap-install. but you need to do a little more try "./smbldap-install all"

---

### Post by Cubicegg on 2006-01-10
hi, thanks but just tried that and the same thing has happened :(

---

### Post by kejar31 on 2006-01-10
i don't have a ubuntu install handy to test for ya. Did you try hitting the return key to see what happens. If I remember correctly defaults are set so if you just hit enter most of the time it will be ok.

It has been a little while since I ran the script. Been spending most of my time writing my own ( Sadly though for another distro. :(  ) but I do include a screenshot by screenshot how to for mine;) . It will soon be ported tu Ubuntu as well to.:cool: :cool: 

check it out here [ftp://ns1.facettech.com/AVA-INSTALL-HOWTO.pdf](ftp://ns1.facettech.com/AVA-INSTALL-HOWTO.pdf)

---

### Post by Cubicegg on 2006-01-10
hi,

i tell you what, though i like ubuntu, i am not tied to it, why dont i install scientific linux instead and use your script, and perhaps you can offer me some help if i need it as my main purpose (for the moment) in using linux is to setup a pdc so that my current xp machines can use roaming profiles and have user's e-mails stored centrally?

Though I am probably going to move from Xp on the desktop to linux, probably ubuntu as it has a good desktop-user feel.

thanks james

---

### Post by Cubicegg on 2006-01-10
hi,

i tell you what, though i like ubuntu, i am not tied to it, why dont i install scientific linux instead and use your script, and perhaps you can offer me some help if i need it as my main purpose (for the moment) in using linux is to setup a pdc so that my current xp machines can use roaming profiles and have user's e-mails stored centrally?

Though I am probably going to move from Xp on the desktop to linux, probably ubuntu as it has a good desktop-user feel.

thanks james

---

### Post by Cubicegg on 2006-01-10
hi,

i tell you what, though i like ubuntu, i am not tied to it, why dont i install scientific linux instead and use your script, and perhaps you can offer me some help if i need it as my main purpose (for the moment) in using linux is to setup a pdc so that my current xp machines can use roaming profiles and have user's e-mails stored centrally?

Though I am probably going to move from Xp on the desktop to linux, probably ubuntu as it has a good desktop-user feel.

thanks james

---

### Post by kejar31 on 2006-01-10
my script is still very much a work in progress just an fyi

---

