---
title: "Blacklisting with postfix"
date: 2008-07-11
forum: Server Platforms
---

### Post by tonkyman on 2008-07-11
I've setup a server with Postfix, Courier, MYSQL, Spamassassin and squirrel mail. I have several RBL's setup in the main.cf file of postfix and I'm using postgrey to for greylisting.

My question is: is there a way to manually blacklist a domain or a user from a domain?? I thought there may be a way to have postfix read a flat file or database entry and drop mail coming from places that are in the flat file.

Any suggestions??

Thanks,
Tony

---

### Post by hyper_ch on 2008-07-11
there is :)

have a look at the sender_checks and sender_checks_pcre

[http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt](http://jimsun.linxnet.com/misc/postfix-anti-UCE.txt)

---

### Post by tonkyman on 2008-07-15
hyper_ch, thanks for the link. I read that and it got me to thinking in another direction.

That solution looked overly complicated to me and I remembered reading a paper on SpamAssassin a while back and thought there was a way to blacklist and whitelist from SpamAssassin. There is and it's a very easy solution.

In the etc/spamassassin or /etc/mail/spamassassin directory the is a file called local.cf. This file hold some of the global settings. 

At the very bottom of that file I added:

```
# This is an example of a blacklist entry
blacklist_from username@somewhere.com

# This is an example of a white list entry
whitelist_from username@trustedperson.com
```

That's all there is to it. 

For you WebMin users this can be done from there by clicking on spamassassin and whitelist/blacklist.

There are several versions of these white/blacklist commands and I found them under "Manual Whitelisting" on the Spamassassin web site. You can block or allow parts of ip blocks, whole ip blocks, one person or entire domain. These are very powerful commands.

Good luck,
Tony

---

### Post by tonkyman on 2011-06-02
**[SIZE="3"][FONT="Arial Black"]**UPDATE**[/FONT][/SIZE]**

Since I posted this I have found that it will not work on every server.  Here is how I corrected it on two of my servers and I like it much better.

BTW! It takes longer to read this than it does to implement it so don't be scared off by it.

Blacklist Setup For Postfix

*********************************************************************************** 
This information is from many sources. With the main idea from a post by "crxssi"
on LinuxQuestions.org. 

The forum information provided by "crxssi" would not work for me on my Ubuntu 8.04
server running postfix so I revised it into the following instructions. I have two 
servers running this configuration and working beautifully.

I assume no responsibility if you screw your server up. Make sure you backup all
the files you'll be editing.

Thanks,
Tony
[email]tony@minneapolis-moline.com[/email]
***********************************************************************************  


To make blacklisting easier we will create a shell script that will allow us to type an
email address, ip address, domain or country (eg. pl, cn, br, etc) on the command line
so it can be processed by postfix and rejected. 

First let's create the blank file for our shell script.

Type:

```
pico /usr/local/bin/addblacklist
```

add the following contents by typing the following or by cut and paste:

```
#!/bin/sh

echo -e "$1\tREJECT" >> /etc/postfix/sender_access
postmap /etc/postfix/sender_access 
```

Then save the file.

Next: Change the permissions on the file so it can be executable.

Type:

```
chmod +x /usr/local/bin/addblacklist
```
 
Now you should have a file in the /usr/local/bin/ directory called addblacklist that
has the following permissions rwxr-xr-x or 755

Then make sure you have "check_sender_access hash:/etc/postfix/sender_access" in your 

"smtpd_recipient_restrictions" section (or any section) in /etc/postfix/main.cf

Do this by typing:

```
pico /etc/postfix/main.cf
```

Then find the section that reads "smtpd_recipient_restrictions =" and add the following
line below the "="

```
check_sender_access hash:/etc/postfix/sender_access,
```

The file will look like the file below. *NOTE: your file contents may not be exactly
like the one below. I'm showing it only so you get an idea of what it will look like.

The word (snip) is there to show where I cut the file for this example.
The line we added will not have the "Added Line>>" or "<< Line we added" I just put
that in the file so you could find it easier.
   
(snip)
 smtpd_recipient_restrictions =
             reject_invalid_hostname,
             reject_unknown_recipient_domain,
             reject_unauth_pipelining,
             permit_mynetworks,
             permit_sasl_authenticated,
             reject_unauth_destination,
Added Line>> check_sender_access hash:/etc/postfix/sender_access, << Line we added
             check_policy_service inet:127.0.0.1:60000,
             reject_rbl_client multi.uribl.com,
             reject_rbl_client dsn.rfc-ignorant.org,
             reject_rbl_client sbl-xbl.spamhaus.org,
             reject_rbl_client cbl.abuseat.org,
             reject_rbl_client combined.rbl.msrbl.net,
             permit
 transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
(snip)

Save the file and at the command line type:

```
postfix reload
```

This will reload and refresh the post fix settings.

All you need to do is type:
```
addblacklist [email]XXX@XXXX.XXX[/email]
``` and hit enter. 

You can name the script anything you want. "blacklist" "badip" etc. It will append the email address you typed with REJECT in your sender_access file and postmap it. This will stop the email address from connecting to Postfix and thus reject any mail sent to your user by the blacklisted user.

This is a pretty neat little script because you can blacklist lots of things. For example:

email addresses:
"addblacklist [email]XXX@XXXX.XXX[/email]" where [email]xxx@xxxx.xxx[/email] is replaced by a real address "spam@example.com". 

This will blacklist this one user "spam@example.com".

Entire domains:
"addblacklist XXXX.XXX" where xxxx.xxx is replaced by a domain "example.com". this will blacklist
all users at "example.com".

Entire countries like .pl .ru .cn:
"addblacklist .XXX" where .xxx is replaced by a .com .net .pl .cn .ru etc. This will blacklist
entire countries like .pl .ru .cn etc.

Enjoy,
Tony

P.S.
You can manually edit the sender_access file, save it and run "postmap sender_access" instead of running blacklist xxx.xxxx.xxx. You can also open the sender_access file and remove someone if you have added them by mistake. Just remember to remove the entire line, save then run postmap.

---

