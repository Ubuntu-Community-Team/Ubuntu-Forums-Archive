---
title: "OpenLdap Install/Config"
date: 2011-02-05
forum: Server Platforms
---

### Post by carlos@idfx on 2011-02-05
First post on any forum relating to Ubuntu Server. Building my first Ubuntu Server, Xubuntu 10.10 Maverick Meerkat. 
Currently working as a sysadmin for a visual effects company in North Hollywood and working diligently to build a machine with OpenLdap, Samba, FTP and VPN capabilities. 

I am A+, Network+ certified with about 15 years of tinkering experience and running small LANs. 
I have no prior experience with Linux except for a little I learned in  the Navy/also where I was exposed to Ubuntu. 
My experience with servers is with Windows platforms (Server2003). 
My biggest challenge so far has been getting the OpenLdap configured. 

I have tried the install method mentioned in the official Ubuntu Server Guide and failed, I have been trying the method on OpenLdap.org and fifty other things including uninstalling and reinstalling slapd a couple of times. 
It seems to me that the install method depends on which distro of Ubuntu your running coupled with which version of OpenLdap. 

My main problems have been based around using ldapadd to add the *.ldif files to the database.
I have successfully added the following files
[COLOR=Blue]sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif[/COLOR]

This morning after some sleep I am back at it and this is my first attempt at continuing with this process. Here are my results. Strangely, I have to say, they are not the same results I was seeing yesterday. 
[COLOR=Blue]root@maverick01:/home/idfxadmin# sudo ldapadd -Y EXTERNAL -H ldapi:/// -f backend.identityfx.com.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
        additional info: <olcModuleLoad> handler exited with 1[/COLOR]

Previous errors were related to permissions mostly (49)(60) I believe.

I hate to say it but I'm a little lost. I can navigate my way through the directory structure and I can do what I need to do to edit files in VI/VIM but there are many things I don't know such as whether or not I have these frontend/backend.ldif files in the right directory to begin with.

If anyone can lend a guiding hand to get me on track with this procedure I am a willing and able student and dedicated to the successful implementation of this server.

Thank you in advance for any and all assistance/guidance regarding these matters,
Carlos

---

### Post by carlos@idfx on 2011-02-05
Second question:
In case it wasn't clear from the post above, I intend to use this server as a PDC to authenticate both Windows and Mac clients. 

I've always been under the impression that the OpenLdap server would perform the role of DC. This may have been a misunderstanding of the capabilities of OpenLdap. 

Having set up only a couple of Domain/Active Directory implementations in WinSrvr2003, I am not clear on which component provided the DC functionality. 

My belief is that it was the "Directory Services" (=OpenLdap) through whose authentication, access to the domain was controlled.

While configuring smb.conf to initially enable some network shares I noticed a lot of language declaring that Samba can be the DC.

Is there a conflict between OpenLdap and Samba?

Can you just leave the Samba DC functionality turned off?

Can you, should you, do you need two levels of authentication?

Which of these tools is better for Client Authentication?

Signed,
Slightly confused

---

### Post by luvshines on 2011-02-06
Though I haven't seen that error, but following post has some troubleshooting tips in comment #6
[http://ubuntuforums.org/showthread.php?p=8154148]("http://ubuntuforums.org/showthread.php?p=8154148")
See if that helps

---

### Post by carlos@idfx on 2011-02-06
> **luvshines said:**
> Though I haven't seen that error, but following post has some troubleshooting tips in comment #6
[http://ubuntuforums.org/showthread.php?p=8154148]("http://ubuntuforums.org/showthread.php?p=8154148")
See if that helps
I appreciate that link. I think I'm going to get through this process. 

I tried to run the string in his step one and failed so I kept reading and on the second page got to the part where he recommended purging and re-installing slapd ldap-utils which I did and then the string ran properly.

So now I'm ready for the second step.

My question is:
Do I need to be in a specific directory when I'm creating the db.ldif or will it just magically know where to go? 

I will wait for a reply before continuing as I don't know if it will nullify my progress to install the db in an incorrect directory.

Thank you for your assistance

---

### Post by carlos@idfx on 2011-02-06
[QUOTE=carlos@idfx;10434141]I appreciate that link. I think I'm going to get through this process. 

I tried to run the string in his step one and failed so I kept reading and on the second page got to the part where he recommended purging and re-installing slapd ldap-utils which I did and then the string ran properly.

So now I'm ready for the second step.

My question is:
Do I need to be in a specific directory when I'm creating the db.ldif or will it just magically know where to go? 

 I went ahead and created the db.ldif and people.ldif docs in the /etc/ldap directory.

Did what I believed to be all the necessary mods to the variables and saved the docs. See attached below. BTW, how do I insert text into a box on this editor instead of attaching or just cutting and pasting?

Then I got stopped at this point:
[COLOR=Blue]
idfxadmin@maverick01:/etc/ldap$ sudo ldapadd -x -D cn=idfxadmin,dc=identityfx,dc=com -w idfxadmin -f people.ldif
ldap_bind: Invalid credentials (49)[/COLOR]

This is an error I saw repeatedly in previous attempts at completing the config process. I suppose I'm choosing some incorrect variable responses?

---

### Post by carlos@idfx on 2011-02-09
> **luvshines said:**
> Though I haven't seen that error, but following post has some troubleshooting tips in comment #6
[http://ubuntuforums.org/showthread.php?p=8154148](http://ubuntuforums.org/showthread.php?p=8154148)
See if that helps

Ok, so I've gone back and "purged" slapd and re-installed it.

Then following the tutorial referenced in the above post, done everything it states, simply copying and pasting the required code into the shell and running it and creating docs with the specified text as stipulated.

Without modifying any of the variables to personalize the database to meet my domain requirements I succeeded in getting all the way to the final step which is querying the database.

What follows is my result.

```
idfxadmin@maverick01:~$ ldapsearch -x -H ldap://admin.home.local -b dc=home,dc=local
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
```

The one thing I changed after cutting and pasting this into my shell was I inserted "admin.home.local" where it had said "dustball.home.local"

I still have not resolved this issue but I will be switching my post to:
[[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1197443#") 				  				[Ubuntu Forums]("http://ubuntuforums.org/index.php")   	> [The Ubuntu Forum  Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support  Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   	> [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")   			 			 				[[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1197443") ** 	[COLOR=#980101][B][ubuntu]**[/COLOR]  ldap_sasl_bind(SIMPLE): Can't contact LDAP server  [/B]
If you find my post here and can help, please find it in the other category and submit your replies there.

Thank you all in advance for your dedication to the community. I love your work.

---

