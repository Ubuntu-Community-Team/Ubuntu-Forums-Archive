---
title: "HOW TO: Server 9.04 Likewise-open5 Samba Integration"
date: 2010-04-21
forum: Server Platforms
---

### Post by cjfarley on 2010-04-21
HOW TO: Server 9.04 Likewise-open5 Samba Integration

Ubuntu Server 9.04
Likewise-Open5
Samba 3.3.2

 I've had all sorts of problems setting this up and I thought there might be other having the same problems.  I needed to have Active Directory users be able to read and write to directories on a Ubuntu Server.  We have a mixed Windows /  Ubuntu environment, so I needed users home directories to be accessible in windows as well.  Below is what I came up with. I hope it helps.

I'm assuming your starting with a fresh install of Ubuntu Server 9.04 with all updates applied. 

In all the config files I only added to what was there, I didn't remove any of the defaults.

I've taken some steps from these 2 guides, but I've also left some steps out.
[http://www.likewise.com/resources/user_documentation/Likewise-Samba-Guide-5.pdf](http://www.likewise.com/resources/user_documentation/Likewise-Samba-Guide-5.pdf) 
[https://help.ubuntu.com/8.10/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ad-integration.html).

1. Install all the needed packages:

*sudo apt-get install samba winbind smbfs smbclient likewise-open5*


2. This is from the ubuntu help:

[I]sudo mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.orig
sudo ln -s /etc/samba/secrets.tdb /var/lib/samba [/I]
    
3. Join your domain with likewise-open5:

*sudo domainjoin-cli join* EXAMPLE.COM DOMAINADMIN

4. Edit your Samba config:

*sudo nano /etc/samba/smb.conf*

   workgroup = EXAMPLE
   security = ads
   realm = EXAMPLE.COM
   idmap backend = lwopen
   idmap uid = 50-9999999999
   idmap gid = 50-9999999999
I made the above changes and didn't change anything else except setting up the shares.

5. Edit your nsswitch config:

*sudo nano /etc/nsswitch.conf*

passwd:         files winbind compat lsass
group:          files winbind compat lsass

6.  Edit your Kerbos config:

*sudo nano /etc/krb5.conf*

Add the kdc line:
[realms]
        EXAMPLE.COM = {
                kdc = ADSERVER.EXAMPLE.COM

[domain_realm]
        .example.com = EXAMPLE.COM
        example.com = EXAMPLE.COM

7. Reboot

8. Join Domain with Samba

*sudo net join EXAMPLE.COM -U DOMAINADMIN*

9. Reboot again

10.  Check winbind status and see if everything is working!

*sudo /etc/init.d/winbind status*

*wbinfo -u   *(this should return all domain users)


At this point everything is working for me.  I can access the shares with a SSO.

If you can't login as domain users you may need to join the domain again with likewise (Step 3), but after that your set.

I'm not sure if all these steps are needed, but this is what I did to get it to work and I've reproduced the results 3 times.  

Enjoy!

**Edit**
After further testing I've found that I can access the shares through ip address but not hostname.  I have no idea why and it isn't a big problem for me.  Just make sure when your testing it out use the IP address NOT the hostname.

---

### Post by flint_ on 2010-09-17
cjfarley,

Thank you for your accurate, and uncomplicated description of how to implement and test Active Directory.

You are a credit to the community.  Keep writing!

Kindest Regards,

Paul Flint

---

