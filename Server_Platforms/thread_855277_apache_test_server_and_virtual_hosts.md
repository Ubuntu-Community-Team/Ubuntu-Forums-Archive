---
title: "apache test server and virtual hosts"
date: 2008-07-10
forum: Server Platforms
---

### Post by Mr_Whippy on 2008-07-10
Hi all,

I am having a few problems here, and wondered if anyone could help.

I have a network setup, 

router = DHCP, DNS, 
nixsrv-01 = apache, fileserver
nixcli-01 = client machine

I am sharing files using nfs, now all this seems to be working fine, however I can only access(view) one of my websites. ill call it siteone.

I access this via FF using the address 192.168.0.5 and thats it, so it would seem that this site has become the default site, if i type 192.168.0.5/siteone i get a 404 error, same for sitetwo. 

so i know that the apache server is working, and as far as i know i have set up both sites to be virtual hosts, i have a site available file for both, they are both enabled, yet i cant see them in the way i thought i would.

do i need to configure them in DNS to work, or something like that, from all the guides i can see i have everything else setup, but it would seem i need to have a DNS server to say goto this server and find the site you are looking for.

any help greatly appreciated.

---

### Post by linux6994 on 2008-07-10
What is the actual ip address of nixsrv-01? Looks like it should be the .0.5 When running a web server its best to run with a static ip to ensure that you have a consistent ip address

---

### Post by linux6994 on 2008-07-10
When running apache your site files will be in /var/www so the 192.168.0.5/siteone will be /var/www/siteone/siteone.html

---

### Post by Mr_Whippy on 2008-07-11
hey linux, 

thanks for the replies, nixsrv-01 is on static ip 192.168.0.5.

and the root for the sites i have moved from www/var to /data/apache/sitename

as i say this seems to work well for siteone, which would seem to have become the default site in some way, if i disable site one in apache, then when i type 192.168.0.5 in my browser i get sitetwo, however when i re-enable siteone i get that again.

I have just tried to access 192.168.0.5/data/apache/sitetwo which is the full path to sitetwo, still no joy, I get the feeling i am missing something that should be really simple here, but not sure what it is.

I am going away for the weekend, but will try to get back on here at some point whilst i am away. 

thanks for any help 

after doing some more reading it would look like i need to set up DNS on my network, that point to the virtual servers could anyone confirm or deny this for me. 

at the moment the DNS i have is just basic from my router.

---

### Post by Mr_Whippy on 2008-07-14
anyone able to help me out any with this please, it is a real pain.

---

