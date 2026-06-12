---
title: "Ubuntu LDAP Authentication"
date: 2007-02-14
forum: Server Platforms
---

### Post by a5benwillis on 2007-02-14
Has anyone gotten Ubuntu to successfully authenticate against LDAP, Novel LDAP to be exact? I am looking for some sort of guide if possible but so far I've only found information for Active Directoy (Kerberos and LDAP).

This is the beginnings of multiple labs in a school district.


Thanks!

Ben

---

### Post by jgmurphy on 2008-01-26
Hi,  Ben I'm looking for pretty much the same thing as you.  Have tried libnss-ldap and pam-ldap packages and my client tries to bind to ldap server (running on Novell netware) but the logs give the error 'Can't bind to ldpap server at 10.5.2.23.  Server not available.  And also the error Cannot bind to any LDAP server as NULL.
The server works for lots of clients running various o/s's 

There's a good starting point here [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Any pointers to more info on this would be great.

Thanks.

---

### Post by drussell13 on 2008-04-02
Hello, has anybody found the solution for this?  I haven't tried the link yet that jgmurphy supplied, but might give it a shot.  But if anybody has found a good way of doing this, I would certainly appreciate it!!
Thanks

---

### Post by drussell13 on 2008-04-02
Hello all, I finally got this working with some help from a few other links.  But below are the steps I took to get it working, Im sure its way off the norm of how your supposed to do it, in fact, I'd love to hear of some other solutions if anyone has any of a possible easier way.  

1. apt-get install libpam-ldap libnss-ldap nscd
    - During install, it will bring you up to a wizard...I did the following....
 a.    IP address / hostname of the LDAP server.- "ldap://10.x.x.x
 b. The search base of your LDAP domain.
 c.  LDAP Version- Probably should be 3
 d.  A screen titled "Configuring LIBNSS-LDAP will appear with only the "OK"
 e.  On the next screen you'll be asked if you want to make root the DB admin. (I have no clue what this does so I just hit no.
 f.  Now you'll be asked whether the DB requires logging in. I said  "No"
 g.  You'll be asked for the root login account for LDAP. (I just put in my admin credentials from Netware- I think its irrelevant cause it didn't do anything for me) 
  h. Then the password for that account. 
 *** Im going to go back through this and see what that actually does, cause in    my setup, I don't think any of that info is used??****

2.  Once you get done with that, I added some lines to pam.d (/etc/pam.d)
 a. common-account
         -  account sufficient      pam_ldap.so
            account required        pam_unix.so

 b. common-auth
         - auth    required        pam_unix.so nullok_secure

 c. common-session
            session           sufficient      pam_ldap.so
            session 	      required        pam_unix.so

e. common-password
           password        sufficient      pam_ldap.so
***Don't know if all of those are absolutely needed, but it works for me, so I kept them all in there ****

3. Next, edit nsswitch.conf  (/etc/nsswitch.conf)
Using vi, you can just type the following.....
:%s/compat/files ldap/g
***Basically the top three lines, passwd, group, shadow should read  "files ldap"

4. Being that I still don't know what that ldap wizard did for me, I manually edited /etc/ldap.conf.    Here are the important lines...
host   10.x.x.x   (Enter your ldap servers IP)
base  o=myorginization  (Put your organization here)
ldap_version 3   (This should already be there)
bind_dn   cn=ldapproxy, o=orginization    (I will talk about this further down)
bindpw  my_password   (I will talk about this further down)
comment out the rootbinddn line
bind_policy soft   (Change from hard to soft here)
pam_password  md5   (Should already be there)
nss_map_attribute       userPassword authPassword  (Manually added where it has the "Necessary for NDS part)
#pam_password clear_remove_old  (Comment this line out)
pam_password nds   (Manually added where it has the "Neccessary for NDS part)
(These next few lines are all under OpenLDAP SSL mechanism)
#ssl start_tls
ssl no
nss_base_passwd o=orginization
nsss_base_shadow o=orginization
nss_base_group  o=orginization
pam_filter      objectclass=posixAccount 

A few notes, I could not get this to work unless I made an "ldapproxy" user in NDS.  Basically I just made the user, gave him rights all the way down the tree, and gave him a password.  You can bind anonymously, but I had complaints from DNS about a null password for that user??  

I also made each Netware account have a "Unix Profile".  That goes a little beyond the scope of this, but let me know if you need help with that.

I hope this helps some people out.  Like I said, Im sure there are easier/better ways, but this worked for me and just thought I'd share.
Thanks

---

### Post by drussell13 on 2008-04-02
One thing to note.....Im noticing that with this solution I just provided, my system is having a hard time with "local authentication".  For example, if I type $sudo whatever_command    and it asks for my password, I have to type it in a couple times before it will register..... Anybody have any ideas on that?? 
Thanks

---

### Post by sgla1 on 2008-04-09
> **a5benwillis said:**
> Has anyone gotten Ubuntu to successfully authenticate against LDAP, Novel LDAP to be exact? I am looking for some sort of guide if possible but so far I've only found information for Active Directoy (Kerberos and LDAP).

This is the beginnings of multiple labs in a school district.


Thanks!

Ben

Doesn't Novell have a NDS client for Linux?  Even a Suse rpm could be rebuilt for Ubuntu, I would imagine.

Of course you could ask Novell for help.  You are a paying customer for Edirectory, right?  Buwahaha...

Other option:
1) get a trial version of sles 10 and install 1 workstation
2) use yast to connect to your Edirectory server
3) look at your pam configs and which libraries are installed on sles, then duplicate the settings to Ubuntu.

---

### Post by sgla1 on 2008-06-08
> **drussell13 said:**
> One thing to note.....Im noticing that with this solution I just provided, my system is having a hard time with "local authentication".  For example, if I type $sudo whatever_command    and it asks for my password, I have to type it in a couple times before it will register..... Anybody have any ideas on that?? 
Thanks

There is a version of sudo compiled with ldap support.  See [http://packages.ubuntu.com/hardy-updates/sudo-ldap](http://packages.ubuntu.com/hardy-updates/sudo-ldap) for the hardy version; there are also versions available for other versions of ubuntu.

If you run the AuthClientConfig tool as per the instructions here: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) it will configure the necessary pam modules for ldap authentication.  In hardy at least, /etc/pam.d/sudo just incudes other pam.d files so you should be all set.

w00t

---

### Post by decoherence on 2008-06-23
My problem is with the homeDirectory attribute, which is overloaded by both the NDS style home and the UNIX style home.

Is there a way to get the ldap client to check the second value of the attribute rather than the first?

Are there reasons to export the NDS-style home path via LDAP? (i know, ask my novell administrator... just wondering if eDir2AD or something needs it...)

Things work perfectly if I cheat and take advantage of an unused, unrelated LDAP attribute to store my home information and re-map the linux client to use that. Instead of getting my home from homeDirectory I get it from apple-user-picture. But I'd prefer to do things "properly."

Can anyone shed any light on how to work with that homeDirectory attribute?

---

### Post by neurovish on 2008-07-07
> **decoherence said:**
> My problem is with the homeDirectory attribute, which is overloaded by both the NDS style home and the UNIX style home.

Is there a way to get the ldap client to check the second value of the attribute rather than the first?

Are there reasons to export the NDS-style home path via LDAP? (i know, ask my novell administrator... just wondering if eDir2AD or something needs it...)

Things work perfectly if I cheat and take advantage of an unused, unrelated LDAP attribute to store my home information and re-map the linux client to use that. Instead of getting my home from homeDirectory I get it from apple-user-picture. But I'd prefer to do things "properly."

Can anyone shed any light on how to work with that homeDirectory attribute?

It's really up to your novell admin.  I don't think it's required for anything, but it is very likely used for something if it is there. Since your apple-user-picture is your home directory, it sounds like you can edit your user attributes.  Where is your NDS style home directory defined?  The place I would expect to see it is in Environment under the General tab (iManager speak), but this doesn't come through in an ldapsearch when I put something in there.  My real home directory is set in the Linux Profile tab.

---

