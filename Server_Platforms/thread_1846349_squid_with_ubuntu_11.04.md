---
title: "squid with ubuntu 11.04"
date: 2011-09-18
forum: Server Platforms
---

### Post by !! hack-back !! on 2011-09-18
hello,
i install ubuntu 11.04 64 bit server package 
i want to install lusca but i didnt find work tutorial to it so any help in this domain please ??

and whats about the zph patch for the kernel 
[http://zph.bratcheda.org/linux-2.6.35-zph.patch](http://zph.bratcheda.org/linux-2.6.35-zph.patch)
how i can patch it with my kernel ????

---

### Post by !! hack-back !! on 2011-09-19
any help pleasssssseee

---

### Post by Dangertux on 2011-09-19
Following this should help you install Lusca-HEAD from source.

[http://blogku-apik.blogspot.com/2011/05/install-lusca-head-on-ubuntu-1104.html](http://blogku-apik.blogspot.com/2011/05/install-lusca-head-on-ubuntu-1104.html)

---

### Post by !! hack-back !! on 2011-09-20
can you tell me please what is the commands to compile in zph patch ??

man i make this [http://blogku-apik.blogspot.com/2011/05/install-lusca-head-on-ubuntu-1104.html](http://blogku-apik.blogspot.com/2011/05/install-lusca-head-on-ubuntu-1104.html)
but when i finish no thing happen so i cant start lusca and it didnt work i dont know what the problem exactly but its not working ...

---

### Post by SeijiSensei on 2011-09-20
What the heck does any of this have to do with squid??

---

### Post by !! hack-back !! on 2011-09-20
thank you [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") for replay but what u mean exactly ??

---

### Post by Dangertux on 2011-09-20
@SeijiSensei - Lusca is a fork of squid, alot of the codebase is the same, I'm guessing that's what it has to do with squid.

@!! hack-back !! - it might be easier if you tell me what you did when trying to compile the Lusca-HEAD software.

---

### Post by !! hack-back !! on 2011-09-20
the last thing i did for patching is in this link
[http://www.vivaolinux.com.br/dica/Instalando-Squid-2.6-+-patch-ZPH-no-Debian-Etch](http://www.vivaolinux.com.br/dica/Instalando-Squid-2.6-+-patch-ZPH-no-Debian-Etch)
but for 3.1 squid

but man if u helped me to install lusca so its not important then to install squid because lusca is more better and important than normal lusca ... its the development for squid

can i talk to u live ??

---

### Post by !! hack-back !! on 2011-09-20
any way now iam formatting my server and i wish that u can help me now to finish it and i know its not that impossible and hard thing for professional person in linux ...

---

### Post by Dangertux on 2011-09-20
Ok I see what you're trying to do now, you're not going to need to patch your kernel for this.

You will however need to patch the Lusca source with the zph patch. Sorry if this has been a little confusing. I am not very familiar with Lusca and only deal with Squid rarely. So bare with me a little :-)

The tutorial you have is for patching squid, not lusca, however since Lusca is a fork of squid the patch should work (note the should). Basically you already have the Lusca source since it doesn't come as a prepackaged binary.

In order to patch Lusca following that tutorial you should be able to follow this portion of the tutorial

```

**# cd squid-2.6.5** 

 Aplicando o patch: 

**# patch -p1 < ../squid-2.6.STABLE2-ToS_Hit_ToS_Preserve.patch** 

 E por último e mais simples de todos vamos criar os pacotes .deb a  partir dos fontes que baixamos, mas agora já com o patch ZPH aplicados: 

**# dpkg-buildpackage -rfakeroot -uc -b** 

 Feito isso vamos ter os seguintes pacotes em /usr/src: 
[LIST]
[*] squid_2.6.5-6_i386.deb
[*] squid-cgi_2.6.5-6_i386.deb
[*] squidclient_2.6.5-6_i386.deb
[*] squid-common_2.6.5-6_all.deb
[/LIST]

 Daí é só instalar: 

**# dpkg -i squid*** 

```*note sorry for the spanish , but that's what the tutorial you linked was in.

However in order to do that you need to package the Lusca-HEAD source first.  In order to create the deb package you can use this 

```

sudo checkinstall -D

```
instead of  make install.

Be sure you substitute the squid source for the lusca source and it SHOULD patch. After that you will end up building it into a package and installing it using dpkg. 

That SHOULD give you a running Lusca-HEAD install WITH the zph patch.

*note : I'm ammending my original post so additional readers don't get confused by the kernel patching part.

Also, in response to your PM I don't really use messenger services , and the best way to solve this problem in my opinion is to deal with it on the forum so that other individuals in the future may find an answer to a similar problem.

---

### Post by !! hack-back !! on 2011-09-20
thanks man for replaying but the link i attached not work with me so now i want to forget patching
i just need to install the lusca and work fine no thing either that !!
so how i can install lusca to make it work fine on my server ....
thats my question before any thing else like patching the kernel

---

### Post by Dangertux on 2011-09-20
OK here you go, tested it in a VM running 11.04 server it works if you follow this. You can even copy and paste if you'd like.

Step 1 : Download Source for Lusca-HEAD

```

http://lusca-cache.googlecode.com/files/LUSCA_HEAD-r14809.tar.gz

```Step 2 : Extract Source

```

tar xzvf LUSCA_HEAD-r14809.tar.gz

```Step 3 : Satisfy Dependencies

```

sudo apt-get update
sudo apt-get install gcc build-essential sharutils ccze libzip-dev automake1.9

```Step 4 : Configure and Compile Source

```

cd LUSCA_HEAD-r14809
./configure --prefix=/usr/local/squid
sudo make all
sudo make install

```
Step 5 : Create squid user and group
```

sudo useradd squid
sudo groupadd squid 

```*note you will not likely need to create the group it should already be created.

Step 6 : Editing squid.conf

```

sudo nano /usr/local/squid/etc/squid.conf

```add the following lines

```

cache_effective_user squid
cache_effective_group squid
include /usr/local/squid/etc/tuning.conf

```
Step 7 : Editing tuning.conf

```

sudo nano /usr/local/squid/var/cache/tuning.conf

```paste the following into the file and save

```

cache_dir aufs /usr/local/squid/var/cache 10000 16 256 
cache_effective_user squid
cache_effective_group squid
client_persistent_connections off
server_persistent_connections on
half_closed_clients off
strip_query_terms off
quick_abort_min 0 KB
quick_abort_max 0 KB
quick_abort_pct 100
vary_ignore_expire on
reload_into_ims on
pipeline_prefetch on
read_timeout 30 minutes
client_lifetime 6 hours
negative_ttl 30 seconds
positive_dns_ttl 6 hours
negative_dns_ttl 60 seconds
pconn_timeout 15 seconds
request_timeout 1 minute
store_avg_object_size 13 KB
log_icp_queries off
ipcache_size 16384
ipcache_low 98
ipcache_high 99
log_fqdn off
fqdncache_size 16384
memory_pools off
forwarded_for on
cachemgr_passwd none all
client_db off
max_filedescriptors 4096
n_aiops_threads 24
load_check_stopen on
load_check_stcreate on
download_fastest_client_speed on
maximum_object_size 3 GB 

```Step 8 : Create directory for caching and Set correct permissions

```

sudo mkdir /usr/local/squid/var/cache
sudo chown squid:squid /usr/local/squid/var/cache

```Step 9 : Create a caching folder

```

sudo /usr/local/squid/sbin/squid -z

```Step 10 : Run Lusca

```

sudo su
su squid
/usr/local/squid/sbin/squid

```

---

### Post by !! hack-back !! on 2011-09-20
i swear i did the same before , but you know just to be sure i will make it now again , 
but can you tell me please how you know that it is work successful ?

---

### Post by !! hack-back !! on 2011-09-20
still waiting you man .... i want to know how u test it please

---

### Post by Dangertux on 2011-09-21
Honestly I'm really not sure where you're getting caught up here. Is there any particular reason you are using this over squid?

---

### Post by !! hack-back !! on 2011-09-21
after all
hb@Net-Gate:~$ sudo su
[sudo] password for hb:
root@Net-Gate:/home/hb# su squid
$ /usr/local/squid/sbin/squid
$


and it not work ....
test in firefox it said 

The proxy server is refusing connections

---

### Post by xcitchx on 2012-08-22
> **Dangertux said:**
> OK here you go, tested it in a VM running 11.04 server it works if you follow this. You can even copy and paste if you'd like.


How to make multi user and pass?
How to make realtime log?
Is it possible lusca listen to sock5 proxy? 
How to uninstall lusca?

Thanks

---

### Post by nothingspecial on 2012-08-23
Hi

Please start a new thread with as much detail about your problem as you can. Include what you have tried and ant errors you get.

This thread is old.

Closed.

---

