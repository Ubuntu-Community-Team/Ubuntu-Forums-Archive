---
title: "Replacing IIS server with Ubuntu LAMP server"
date: 2010-03-07
forum: Server Platforms
---

### Post by vphillips1 on 2010-03-07
I am trying to replace our Intranet Web Server (Win2K / IIS) with an Ubuntu 9.10 LAMP server. Our hosts are Active Directory Domain PC's running XP Pro with IE8. I have been struggling to get "Single Sign On" working for pages that need to be restricted to members of specific AD security groups. Joining Ubuntu to the domain and authenticating an individual AD user with kerberos proved to be fairly easy but it does not satisfy my AD group requirements. It seems to me that this would be a pretty common scenario but I am finding that howto's on this subject are scarce and not very detailed. Has anyone successfully gotten this working on 9.10 and if so, which Apache modules did you end up using? A nudge in the direction of a really good tutorial on the subject would be very much appreciated.

---

### Post by R.Bucky on 2010-03-07
I am not aware of any Apache modules that function interactively with AD DS. Samba 5 will have a better interaction with AD DS is the future, but that is not what you are after. I authenticate Ubuntu 9.10 with AD, but Apache and the XP clients are two different systems all together. 

I suggest that you control access to web pages or content with a CMS or on an ip basis. If your AD groups are restricted to a certain ip range, it would be easy enough to write a simple .htaccess file and restrict access in that manner, making authentication somewhat of a moot point.

---

### Post by spynappels on 2010-03-08
But that would not help if users may sign in from different workstations at different times.

Example:  A work station in a Hospital LAN where a doctor may log in in the morning and have access to certain pages, but a secretary may log in from the same machine later in the day using her own AD cred. but she should not have access to those pages.

Could AD not be used to restrict access on an Apache Webserver?

---

### Post by R.Bucky on 2010-03-08
I found this article ([http://www.debianhelp.co.uk/apachead.htm](http://www.debianhelp.co.uk/apachead.htm)). Perhaps, it may be of some help. Otherwise...

---

### Post by koenn on 2010-03-08
> **spynappels said:**
> .

Could AD not be used to restrict access on an Apache Webserver?

Yes, it can. 
You're probably looking for this:
[http://httpd.apache.org/docs/2.0/mod/mod_auth_ldap.html](http://httpd.apache.org/docs/2.0/mod/mod_auth_ldap.html)

but keep in mind that MS's implementation of LDAP, AD, does not always follow the standard so it can be quite tricky. 

I've played with this for a while and got as far as managing access based on users, but not groups.  

This seems to be going in the right direction:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html)

---

### Post by vphillips1 on 2010-03-09
Since my original post I have made a little headway on the project. Using the Apache ldap module and the following .htaccess file I can allow access to a directory only for users in the WWW_1 Active Directory security group.
--------------------------
AuthType Basic
AuthBasicProvider ldap
AuthName "WWW_1 Authorization"
AuthzLDAPAuthoritative Off
AuthLDAPUrl "ldap://example-dc1:3268/dc=example,dc=ex?sAMAccountname??(objectClass=*)"NONE
AuthLDAPBindDN [email]administrator@example.ex[/email]
AuthLDAPBindPassword xxxxxxxx
AuthLDAPGroupAttributeIsDN on
require ldap-group cn=www_1,cn=Users,dc=example,dc=ex
---------------------------------
I still get prompted for the username and password though. I was hoping that Internet Explorer would pass the credentials of the logged on user for me and accomplish true Single Sign On for the users.

---

### Post by koenn on 2010-03-10
cool. (I'll save that config just in case I ever want to have another go at it)

For the  SSO - I wonder : is it that IE doesnt pass on the credentials, or that Apache doesn't process them and comes with a prompt instead ? 
On an IIS, that would be "Integretad Authentication" or so. I wonder if Apache has anything like that.

---

### Post by terazen on 2010-03-10
I don't think IE attempts to login at all by default except ftp sites where it tries "anonymous".

---

### Post by koenn on 2010-03-11
> **terazen said:**
> I don't think IE attempts to login at all by default except ftp sites where it tries "anonymous".

it does, 
it's an option you can configure somewhere in IE options -> Security. 
Among the choices are 'anonymous', prompt, use windows logon credentiuals, ...

---

### Post by haydeniv on 2012-08-30
This is a little old but for those wondering how to get IE to pass windows credentials, you need to add your domain name to the Local intranet security zone under Tools > Options > Security Tab > Sites > Advanced.  Only Internet Explorer would be so convoluted and bury a config that deep.  You can also have your Windows admin set this in group policy so you do not need to change every single workstation.

See: [http://technet.microsoft.com/en-us/library/dd572939%28v=office.13%29.aspx]("http://technet.microsoft.com/en-us/library/dd572939%28v=office.13%29.aspx")

---

### Post by sandyd on 2012-08-31
***Necromancing - thread closed.***

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

