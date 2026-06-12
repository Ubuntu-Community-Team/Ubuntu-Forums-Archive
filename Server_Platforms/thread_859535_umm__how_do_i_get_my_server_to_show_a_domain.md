---
title: "umm  how do i get my server to show a domain"
date: 2008-07-14
forum: Server Platforms
---

### Post by chuck jessup on 2008-07-14
umm  how do i get my server to show a domaininstead of my ip address... i have forwarded the domain to my server ip address which works, however i would like it to show the domain, instead of my dsl ip address... a co worker told me that tehre was a config file i needed to edit but for the life of me i couldnt remember what it was, the co worker doesnt remember the file to edit, so any help i could get would be like greatly welcomed...

Jesse Fender

---

### Post by k_grdn on 2008-07-14
Hi,

What does a dig show for your fqdn?

dig @nameserver `hostname -f`

You can set the local hostname in /etc/hosts

Regards,

k_grdn

---

### Post by chuck jessup on 2008-07-14
'a dig'? the site is for a game that i play... i have it set up so that when you type in  [www.mydomain.com](www.mydomain.com) it goes to my servers 'test' page, but in the address bar instead of [www.mydomain.com](www.mydomain.com) it shoes 555.444.33.22... how do i mask that so that it shows [www.mydomain.com](www.mydomain.com) instead of the ip address? 
Jesse Fender

---

### Post by windependence on 2008-07-15
Post your apache config file, I think I know what is wrong.

-Tim

---

### Post by chuck jessup on 2008-07-15
i use web min, which is really starting to get on my nerves. i cant find get my apache config file (or i dont know how on webmin...) i am haveing so much trouble with this... this is a minor thing atm getting my ftp and mail server working correctly- that has taken absolute priority. ill be posting on that here in a minute... webmin isnt saving my configurations either which is the most annoying thing in the whole world... 

do you know how to get to the config file on webmin 1.420?

Thanks,
Jesse Fender

---

### Post by chuck jessup on 2008-07-15
ummm if you tell me what you think it is wind - i can edit the conf file on my server directly.... please let me know...
i just reinstalled the server and it is still issuieing the ipaddress instead of [www.mydomain.com](www.mydomain.com)

Jesse Fender

---

### Post by cariboo on 2008-07-16
To post your apache2.conf file, ssh into your server then:

```
cat /etc/apache2/apache2.conf
```

Highlight the output, open a text editor and use either the wheel on your wheel-mouse or click both mouse buttons at the same time to paste the output into a text editor. This is assuming you're accessing your server from a computer with a linux distribution installed.

If you are using windows the above won't work:) What you could do is pipe the output to a text file:

```
cat /etc/apach2/apache2.conf > /home/<yourusername>/apache2.conf
```

Where <yourusername> = your user name.

Then use sftp or scp to download it to your computer.

I'm there a lot of different ways to do this.

Jim

---

### Post by windependence on 2008-07-16
> **chuck jessup said:**
> ummm if you tell me what you think it is wind - i can edit the conf file on my server directly.... please let me know...
i just reinstalled the server and it is still issuieing the ipaddress instead of [www.mydomain.com](www.mydomain.com)

Jesse Fender


There is a server name directive in your apache.conf file. You probably have this set to the IP address instead of the domain name. 

See, this is the problem with GUI front ends as you have found out. You don't really know what is going on, and when there is a problem, you are lost. Learn the CLI. You will be glad you did, trust me. I have been where you are, and got the T-shirt. :)

-Tim

---

### Post by chuck jessup on 2008-07-16
ok... thats great... i have an issue... i have nano installed and it wont allow me to save the file... chmod anything and i end up having to re install the server...which needless to say is like a pain to do... gedit wont display config files... have been doing better in the cli, and use it more extencively than webmin. (its nice to have the option to go either or... which is nice for ones switching to *nix from windows...)... im rambling ... im sorry... just way to frustrated...

Thanks Tim, i will look into that when i get off work :)

Jesse Fender

---

### Post by Dillio187 on 2008-07-16
you can't save anything because you're trying to save to a directory your user account has no permission to.  Launching nano using sudo will fix this (but be VERY careful!!)

sudo nano /var/www/apache2.conf

it will then prompt for your password to elevate privledges.

---

### Post by chuck jessup on 2008-07-16
OK Thanks! that helps me soo very much! Thank you thank you thank you thank you... 

that will help save me from chmod issues. and having apache chash on me. :D

Jesse Fender

---

### Post by chuck jessup on 2008-07-17
ok, i was able to get into teh config files and still was unable to find the server address directive line Tim. none of the apache config files had such a thing. the server still showing the ip address. i will give it another shot when i get the opertunity.

Jesse Fender

---

### Post by windependence on 2008-07-17
It should be in your apache2.conf file. If not, insert it before or after the ServerAddress directive like so:

ServerName [www.example.com](www.example.com)

Don't forget to save the file and restart Apache. Also, Apache gets the server name by reverse lookup of the IP so if you do not have an alias set up in /etc/hosts, it wouldn't be a bad idea. Also, your hostname should match. Check /etc/sysconfig/network. There should be a link like this:

```
HOSTNAME="mybox.mydomain.com"
```

If not, add one.

-Tim

---

### Post by chuck jessup on 2008-07-18
> **windependence said:**
> It should be in your apache2.conf file. If not, insert it before or after the ServerAddress directive like so:

ServerName [www.example.com](www.example.com)

Don't forget to save the file and restart Apache. Also, Apache gets the server name by reverse lookup of the IP so if you do not have an alias set up in /etc/hosts, it wouldn't be a bad idea. Also, your hostname should match. Check /etc/sysconfig/network. There should be a link like this:

```
HOSTNAME="mybox.mydomain.com"
```

If not, add one.

-Tim

ok Tim the apache2.conf dosent have a server name directive at least that i could see, i have gone through it over and over and couldnt find it. i also am cli only and have bought books on admin ubuntu servers and email servers, so i figgured that might make you a little bit happy :P

I will take a look at the /etc/sysconfgig/network to see if it exists... 


Thanks for the further info,

Jesse Fender

---

### Post by chuck jessup on 2008-07-18
/etc/sysconfig/networks dosent exist. adding ServerName to apache2.config made no difference, and when i opened my /etc/hosts file it showed this: (i am on a seperate computer atm so i am typing it to this page....) past the opening line....

```
#...
order hosts,bind
multi on
127.0.0.1       localhost
76.236.31.147:80 (was 127.0.1.1 i changed this to the router outbound ip address)       destructionreborn.com.com      destructionreborn.com

#the following lines are desireable for IPv6 capable hosts
::1       ip6-localhost   ip6-loopback
fe00::0   ip6-localnet
ff00::0   ip6-mcastprefix
ff02::1   ip6-allnodes
ff02::2   ip6-allrouters
ffo0::3   ip6-allhosts

```
the closest thing that i found where it felt right to put the 'ServerName'

```
ServerRoot "/etc/apache2"
ServerName "www.destructionreborn.com" 
```
(i attempted with out the quotes too no change)

and i have a question the server has a 'PID' file it told me that i should direct this file to /etc/apache2/envvars - did i mess something up by the following?
```

PidFile ${/etc/apache2/envvars}

```
help me pls....

Jesse Fender

---

