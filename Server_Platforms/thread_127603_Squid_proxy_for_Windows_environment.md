---
title: "Squid proxy for Windows environment"
date: 2006-02-09
forum: Server Platforms
---

### Post by ariek on 2006-02-09
Hi,

I have been searching for a howto install Samba NTLM & Squid, but unfortunately haven't been able to get my config up & running.

The documentation I have used for Samba with NTLM/Winbind usage for Active Directory authentication:
[http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active]("http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active")

The documentation I have used for Squid with Active Directory authentication:
[http://www.squid-cache.org/Doc/FAQ/FAQ-23.html]("http://www.squid-cache.org/Doc/FAQ/FAQ-23.html")

My syslog tells me that there are ntlm problems:
[B]squid[15593]: WARNING: ntlmauthenticator #1 (FD 8) exited
squid[15593]: Too few ntlmauthenticator processes are running
squid[15593]: The ntlmauthenticator helpers are crashing too rapidly, need help![/B]
However, when I test the connection with the Active Directory (2003) with wbinfo -t everything seems to be fine. Also, when I check the membership of the Ubuntu server in the Active Directory there is no problem.
It would be great find a proper howto for an Ubuntu configuration.

The following is the content of my squid.conf

```
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
http_port 8080

auth_param ntlm program /usr/lib/squid/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm children 30
auth_param ntlm max_challenge_reuses 0
auth_param ntlm max_challenge_lifetime 2 minutes

auth_param basic program /usr/lib/squid/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours
external_acl_type nt_group ttl=0 concurrency=5 %LOGIN /usr/lib/squid/wbinfo_group.pl

acl our_networks src 10.200.7.0/24
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl purge method PURGE
acl CONNECT method CONNECT
acl AuthorizedUsers proxy_auth REQUIRED

http_access allow all AuthorizedUsers
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access allow our_networks
http_access deny all
http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid

```

Could anyone help me please?

Thanx

Arie

---

### Post by baastie on 2006-02-09
Hi,

I think the rights for squid / proxy  are not correct for accessing the ntlm helper files.

Grtz

---

### Post by ariek on 2006-02-10
If you will have a look at the files in /usr/lib/squid/ directory. I think this should be alright.
> [FONT=Courier New]-rwxr-xr-x  1 root  root   13224 2005-09-30 22:43 digest_pw_auth
-rwxr-xr-x  1 root  root   12044 2005-09-30 22:43 diskd
-rwxr-s---  1 proxy shadow  7120 2005-09-30 22:43 getpwnam_auth
-rwxr-xr-x  1 root  root    5164 2005-09-30 22:43 ip_user_check
-rwxr-xr-x  1 root  root   16112 2005-09-30 22:43 ldap_auth
-rwxr-xr-x  1 root  root   31904 2005-09-30 22:43 msnt_auth
-rwxr-xr-x  1 root  root   10148 2005-09-30 22:43 ncsa_auth
-rwxr-xr-x  1 root  root   42280 2005-09-30 22:43 ntlm_auth
-rwxr-s---  1 proxy shadow  9956 2005-09-30 22:43 pam_auth
-rwxr-xr-x  1 root  root    1079 2005-09-30 22:43 RunCache
-rwxr-xr-x  1 root  root      12 2006-02-10 06:26 shellwords.pl
-rwxr-xr-x  1 root  root    8832 2005-09-30 22:43 smb_auth
-rwxr-xr-x  1 root  root    2287 2005-09-30 22:43 smb_auth.sh
-rwxr-xr-x  1 root  root   14256 2005-09-30 22:43 squid_ldap_group
-rwxr-xr-x  1 root  root    5640 2005-09-30 22:43 squid_unix_group
-rwxr-xr-x  1 root  root    3336 2005-09-30 22:43 unlinkd
-rwxr-xr-x  1 root  root   11932 2005-09-30 22:43 wb_auth
-rwxr-xr-x  1 root  root   10304 2005-09-30 22:43 wb_group
-rwxr-xr-x  1 root  root    1333 2006-02-10 06:37 wbinfo_group.pl
-rwxr-xr-x  1 root  root   18060 2005-09-30 22:43 wb_ntlmauth
-rwxr-xr-x  1 root  root    7880 2005-09-30 22:43 yp_auth
[/FONT]

---

### Post by baastie on 2006-02-10
Hi,

Your squid is not running as root, but probably as user proxy ( not user : squid as in the squid documentation ). The proxy user and group are made by default in Ubuntu

take a look at 

cache_effective_user 

and
 
cache_effective_group 

in your squid.conf they should be set or already set to user : proxy and group : proxy.

You have to give this user the right to the winbindd_privileged pipe

If i'm correct...

Grtz

---

### Post by ariek on 2006-02-10
Hi Baastie,

Thanks for you replies. I am really trying to get this working, it's for a production environment and I would really like to get this going.
Also, I think if this would work on an Ubuntu box, it would be a great asset;-)
I could write a simple howto, so there would be another reason to use this great distro.

Anyway, to keep this as simple as possible, I'm testing it in a VMware situation. It is basically a default Ubuntu 5.10 install, with the server option.
After having followed the Samba howto ([here]("http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active")) in an Active Directory situation howto, I installed squid with apt-get.
Then I changed the squid.conf to the following, the lines in [COLOR=Red]red [COLOR=Black]where added by me manually:[/COLOR][/COLOR]
```

[COLOR=Red]cache_effective_user proxy
cache_effective_group proxy
http_port 8080[/COLOR]
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320

[COLOR=Red] auth_param ntlm program /usr/lib/squid/wb_ntlmauth
auth_param ntlm children 5
auth_param ntlm max_challenge_reuses 0
auth_param ntlm max_challenge_lifetime 2 minutes

auth_param basic program /usr/lib/squid/wb_auth
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours 

[/COLOR]  [COLOR=Red] acl AuthorizedUsers proxy_auth REQUIRED
[/COLOR] [COLOR=Red] acl our_networks src 10.0.0.0/24
[/COLOR] acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https, snews
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
[COLOR=Red]
http_access allow all AuthorizedUsers
http_access allow our_networks[/COLOR]
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid

``` 
As you can see, I now added the cache_effective lines.
After this I changed access to /**var/run/samba/winbindd_privileged/pipe **to proxy : proxy.

Here are the error messages I get in syslog:
```
Feb 10 22:54:31 testproxy winbindd[6280]:   process_loop: Invalid request size from pid 6355: 1304 bytes sent, should be 1824
Feb 10 22:54:31 testproxy winbindd[6280]:   This usually means that you are running old wbinfo, pam_winbind or libnss_winbind clients
Feb 10 22:54:31 testproxy winbindd[6280]: [2006/02/10 22:54:31, 0] nsswitch/winbindd.c:process_loop(748)

``` 
Maybe you are right about access problems, although it's not really clear to me where.

Thanx in advance.

---

### Post by ariek on 2006-02-11
It's running now. There was indeed an authorization problem. The documentation which worked for me:
[http://www.siriusit.co.uk/docs/doc.php?pageID=13&typeID=3](http://www.siriusit.co.uk/docs/doc.php?pageID=13&typeID=3)

---

### Post by baastie on 2006-02-11
Hi Ariek,

Glad to be of help.

I've also got it working at one of my customers sites. I had the same error in the beginning. Now it's up and running for 4 months without problems.

I also put dansguardian on the box to have more ( easier ) control on where people are surfing.

Good to hear you got it working :D 

Grtz

Baastie

---

### Post by ariek on 2006-02-13
Hi Baastie,
Thanks for your attention. I was wondering, are you running the Squid/Samba config on an Ubuntu server as well?
It's working globally, users are checked in the AD. However, when I try to check AD group membership with /usr/lib/squid/wbinfo_group.pl I get errors. It would be great to get this running, and I would make my project complete.
Have you tried to get this running?
If I run the wbinfo_group.pl command manually I get an "error on line 50".

Arie

---

### Post by baastie on 2006-02-13
Hi,

Yeah, got it running on a ubuntu 5.10 server. Samba and squid on the same box.

And the users are checked thru group membership in the AD, what i didn't thought, but does work are ( nested ) groups in groups :).
If that is what you mean.

I almost got the same squid.conf as you. The rule with the wbinfo_group.pl was the same. But didn't work for me, didn't go deeper into that yet. It should work...

But without the ttl=900 and concurrency=70 it works fine for me.

external_acl_type ADS %LOGIN /usr/lib/squid/wbinfo_group.pl
# external_acl_type ADS ttl=900 concurrency=70 %LOGIN /usr/lib/squid/wbinfo_group.pl

acl internet external ADS Internet
http_access allow internet 

and in the file which get checked by the wbinfo_group.pl i got "Internet"
stated with quotes

And in my AD i got an group Internet which is a Domain Local - security group. And i don't know for sure anymore. But the Domain Local was important i believe :-k . Should start on that documentation ... euh... ;) 

Grtz

---

### Post by ariek on 2006-02-14
Hi,

What I meant was that users are checked weather they are a member of the AD. The group membership check I can't get working. It's great to hear someone is actually using Ubuntu for this configuration, because I haven't read/heard anyone else is.
Anyway, the struggle I've had is the **wbinfo_group.pl** script.
When I start the wbinfo_group.pl manually, I get the following error:
```
Undefined subroutine &main::shellwords called at ./wbinfo_group.pl line 50, <STDIN> line 1.
``` 
This is the actual line (50) it is complaining about:
```
($user, $group) = &shellwords;
``` As I'm not known to perl, I wouldn't know were to start.

In the file **shellwords.pl** I have added the line [B]"ProxyUsers"
[/B]
The following I have added to squid.conf:
```
external_acl_type ADS %LOGIN /usr/lib/squid/wbinfo_group.pl
acl internet external ADS ProxyUsers
http_access allow internet

``` But now, these lines make squid crash, so I can't use them. Could you please tell me if you can start **/usr/lib/squid/wbinfo_group.pl **manually, and if you can actually check the group membership  of  a user this way.

I have checked quite a lot of messages in the Squid mailing group, but I think I'm stuck here.

Thanks for your support so far.

---

### Post by baastie on 2006-02-15
Hi Arie,

Sorry for the late reply, didn't check back last night.
I will check the customers site today.

Will get back to you asap.

---

### Post by baastie on 2006-02-15
Hi Arie,

Just checked with the customers site.

You don't have to put the user group in the shellwords.pl file.

The reason squid crashes now is that it can't contact the groups in AD.

You have to create an AD group called ProxyUsers, see my previous post on that it should be domain local ( that worked for me ).

These are the lines in my squid.conf

external_acl_type ADS %LOGIN /usr/lib/squid/wbinfo_group.pl
acl internet external ADS Internet
http_access allow internet

The top one creates an external acl type called ADS which should login with the wbinfo_group.pl script. This script uses the wbinfo command so make sure it can find it.

Then i created an acl called internet which should use the ( just created ) external acl ( type ) ADS to check the AD group Internet.

And finally i created an access rule to allow http_acces to the acl internet.

Sorry I could have been more clear on the naming.

In your case you can use the same external_acl_type rule. The acl rule could be different. For example acl 'whatever name' external ADS 'whatever AD group'.
And than the http_acces would be http_access allow 'whatever name'.

The internetgroep thing i was talking about in previous posts was something from the past. I first made a file in which i stated the groups to allow internet to, and let the wbinfo_group.pl read that file. Now i let it read directly from the AD.

I did not modify the wbinfo_group.pl file or shellwords.pl.

You can check with the wbinfo_group.pl file manually. You just have to put in the right domain name and separator etc. This works for me.

Keep me updated,

Grtz

---

### Post by ariek on 2006-02-16
Hi Baastie (Dutch by any chance?)

I have succesfully changed squid.conf, and squid is running without any errors, which is great :D.
I think the problem had to do with smb.conf. The 2 lines below were different in the howto I used.
```
winbind enum users = yes
winbind enum groups = yes
``` The thing I'm stuck with now is that I get **access denied** when I try to use the proxy. The user is a member of the domain local group called ProxyUsers. I actually can see the proxy is authenicating to the AD, because there is a security event which confirms the fact.
Just to make shore, I've added the squid.conf again.
```
cache_effective_user proxy
cache_effective_group proxy
http_port 8080
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320

auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm children 5
auth_param ntlm max_challenge_reuses 0
auth_param ntlm max_challenge_lifetime 2 minutes
auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours
external_acl_type ADS %LOGIN /usr/lib/squid/wbinfo_group.pl

acl internet external ADS ProxyUsers
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443 563     # https, snews
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
acl AuthorizedUsers proxy_auth REQUIRED

http_access allow internet
#http_access allow all AuthorizedUsers
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid
``` 
Hopefully this is the last hurdle;)

Greetings.

---

### Post by baastie on 2006-02-16
Hi,

Yes Dutch :) , and if I had to guess about you I would also say probably Dutch. Than again, guessing isn’t my strong point.

When you users are hitting the squid proxy, what does your proxy say why they are getting denied?. You can probably find the messages in the access.log file.

Grtz

---

### Post by baastie on 2006-02-16
Hmmm, of je kijkt gewoon even naar het profiel...

We zitten zelfs in dezelfde stad :-D

---

### Post by ariek on 2006-02-20
Hi Baastie,
Group membership checkup is still not working. I'm not sure, but I think it's a winbind problem. Is possible for you to give an example of the config files you've used? squid.conf smb.conf krb5.conf.

Alvast bedankt,

Arie

---

### Post by baastie on 2006-02-23
Hi Arie,

Sorry for the late post.
I will be at the customers site tommorow and wil put the .confs online,

Grtz

Baastie

---

### Post by ariek on 2006-02-23
Hi Baastie,
No problem, I'm looking forward to your information.
Grtz,

Arie

---

### Post by baastie on 2006-02-27
Hi Arie,

Here are the confs you asked for,

Grtz

Baastie

---

