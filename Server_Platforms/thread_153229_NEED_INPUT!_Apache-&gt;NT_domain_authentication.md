---
title: "NEED INPUT! Apache-&gt;NT domain authentication"
date: 2006-03-31
forum: Server Platforms
---

### Post by frobroj on 2006-03-31
I am looking to setup user authentication for an apache server that will validate users on our Windows 2003 Domain. I have seen several different ways of doing this. One of the ways to do this is to use an LDAP module another is the Kerberos module and yet another is the NTLM module. And there is probably more. 

   I would like to see what modules people prefer and why. I can't find any good articles that compare the modules and their functionality. I really have little to no experience with apache and with any of these modules so before I go banging my head against the wall ](*,) I want to make sure I am using the best method for what we are doing.

   THANKS EVERYONE!! Your input is much appreciated!

Jeff M

---

### Post by maphew on 2006-04-12
Yes please! I've been trying to get this to work for quite awhile now and so far have not had much luck. I can't get mod_ntml 1 or 2 to compile properly and the mod_auth_kerb requires more arcane knowledge than I possess.

the most current mod_ntlm page seems to be [http://modntlm.jamiekerwick.co.uk/](http://modntlm.jamiekerwick.co.uk/) 
I've seen a report from an ubuntu user who says he can get v1 to work but not v2.

for kerb, [http://modauthkerb.sourceforge.net/](http://modauthkerb.sourceforge.net/) is well written and a tutorial at [http://www.grolmsnet.de/kerbtut/](http://www.grolmsnet.de/kerbtut/) has a lot of info, but it's beyond me (and appears to require administrator access to the Active Directory domain, which I don't have).

If you can modify your cgi's, there's an ntlm cpan module for Apache2: [http://search.cpan.org/~speeves/Apache2-AuthenNTLM-0.02/](http://search.cpan.org/~speeves/Apache2-AuthenNTLM-0.02/)

The last method I know of is mod_auth_ldap [http://www.muquit.com/muquit/software/mod_auth_ldap/mod_auth_ldap_apache2.html](http://www.muquit.com/muquit/software/mod_auth_ldap/mod_auth_ldap_apache2.html) 
It's well documented but I haven't been able to get very far with it either. I just lack too much background knowledge of how ldap works.

---

### Post by frobroj on 2006-04-13
Cool. Thanks for the input. I will dig into the apache2 auth to see if its what we are looking for. Much apreciated. :)

---

### Post by maphew on 2006-04-20
you're welcome, good luck, and please report back if you get anywhere :)

---

### Post by frobroj on 2006-06-13
Well I just got back to this problem. Too many fires to put out! ;) 

My approach this time it to try to use AuthLDAP to authenticate to Microsoft Windows 2003 AD. 
Note: I have no clue about how to do this and I am trying to piece it together. 
One stumbling block I ran into had to do with base LDAP connectivity. I wanted to get ldapsearch(part of the ldap-utils package) and or my java LDAP browser to connect and return information from the Windows 2003 AD server(Base connectivity first!). Well after banging my head for hours I found that all the examples that were listed on the web had the full DN specified for the user in order to bind to Windows AD. After trying everything else I finally tried the standard "windows" username instead (user@mydomain.com) and Bingo it worked. I am still fighting the AuthLDAP and will update as I get it figured out. But for testing I reccommend using:
ldapsearch -W -x -z 10000 -b "dc=DOMAIN,dc=COM" -D "USERNAME@DOMAIN.COM" -h pdc.DOMAIN.COM -p 3268 -d 9
instead of :
ldapsearch -W -x -z 10000 -b "dc=DOMAIN,dc=COM" -D "cn=USERNAME,cn=Users,dc=DOMAIN,dc=COM" -h pdc.DOMAIN.COM -p 3268 -d 9

Hope this little bit helps. One step at a time.
Jeff M

---

### Post by frobroj on 2006-06-16
Ah Ha!! 
Its a good thing I am not a scientist. I managed to change the conditions of the test while I was trying to get it to work... Oops. 
However I did finally get it to work with the following config in my apache2 conf file:

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                Order Allow,Deny
                Allow From All
                AuthName "Chemeketa Network"
                AuthType Basic
                AuthLDAPBindDN "cn=ADUSER,ou=Users,dc=DOMAIN,dc=COM"
                AuthLDAPBindPassword "PASSWORD"
                AuthLDAPURL "ldap://LDAPSERVER:3268/dc=DOMAIN,dc=COM?samAccountName?"
                #require valid-user
                require group cn=GROUP,cn=Groups,dc=DOMAIN,dc=COM
        </Directory>

It works fantastically and the group authentication is sweet!
Hope this helps! 

PS - Another reason I went with this module was that it was installed by default in my ubuntu apache2 installation. That indicates to me that its here to stay and will be supported for a time.

JM

---

### Post by maphew on 2006-06-22
I'm glad it works for you! I'm still out in the cold though. There must be something different about our setup. Thanks for the tip about using [email]username@domain.com[/email] syntax, I now can get ldapsearch to work, so at least I'm a little farther down the road. My apache error logs have changed from "ldap_search_ext_s() for user failed][Operations error]" to "[User not found][No such object]". So I'm pretty sure am connecting the ldap server olay, now I just have to figure out what object apache _is_ looking for.

---

### Post by frobroj on 2006-06-22
Matt - One thing you may want to give a try is to download an ldap browser like  this one: [http://www-unix.mcs.anl.gov/~gawor/ldap/](http://www-unix.mcs.anl.gov/~gawor/ldap/) 
It was very helpful for me. I had an error in one of my strings where I thought it should have been a cn= but it was an ou=. The browser will let you graphically surf to the item and when you click on the item in the left pane you can see its full path in the right pane. 

Hope that helps.
Jeff

---

### Post by hendro on 2006-09-20
How to install mod_ntlm ? apt-get install apache2...?
TIA.

---

### Post by frobroj on 2006-09-21
Hendro,
   
    For the configuration above we used the auth_ldap module not the mod_ntlm module. To determine if you have it available type "ls /etc/apache2/mods-available". This will show you what modules are available. One of the reasons I used the auth_ldap module was that it came with the base apache2 package install and there was no extra package install needed. I always try to keep to the mainline modules so that I dont have to worry about support down the road. 
    Hope this helps. 

Jeff

---

### Post by clutterskull on 2006-11-02
I have successfully compiled and installed mod_ntlm in Apache 2. I'll repost my steps here in case anyone else comes up against this problem. These steps were taken from [http://blognote-info.com/index.php?2006/01/11/345-apache2-et-mod_ntlm](http://blognote-info.com/index.php?2006/01/11/345-apache2-et-mod_ntlm) and the authorization config was taken from [http://plone.org/documentation/how-to/singlesignonwindowsdomains](http://plone.org/documentation/how-to/singlesignonwindowsdomains)

On to the good stuff. The following steps compiled, installed, and enabled mod_ntlm for Apache 2 on my Dapper server. It doesn't matter where you run the commands from; I used ~.

```

mkdir ntlm && cd ntlm 
wget http://modntlm.jamiekerwick.co.uk/ntlm2.tar.gz 
tar -zxvf ntlm2.tar.gz 
sudo aptitude update 
sudo aptitude install apache2-prefork-dev gcc-3.4 
sudo ln -fs /usr/bin/gcc-3.4 /usr/bin/gcc
sudo apxs2 -i -c mod_ntlm.c
sudo make clean 
sudo echo "LoadModule ntlm_module /usr/lib/apache2/modules/mod_ntlm.so" > /etc/apache2/mods-available/ntlm.load 
sudo a2enmod ntlm 
sudo /etc/init.d/apache2 force-reload 
sudo ln - fs /usr/bin/gcc-4.0 /usr/bin/gcc

```

Next, put the following in a <Directory> section of your configuration (such as /etc/apache2/sites-available/default):
```

  AuthType NTLM
  NTLMAuth on
  NTLMAuthoritative on
  NTLMDomain YOURDOMAIN
  NTLMServer yourDomainController
  NTLMBackup yourBackupDomainController
  Require valid-user

```

You may need to restart the server again, but when it comes back up, you should be authenticating against your domain controller. The current logged in username is available in PHP as $_SERVER['REMOTE_USER' ]

I've also included my compiled mod_ntlm.so file in case someone else would find that helpful. Good luck!

---

### Post by jmflyer on 2007-01-02
Just as an FYI for people using auth_ldap...  It uses basic authentication, which sends the username/password cleartext in each header (since tcp is stateless).

NTLM (Either Authen or mod) would be a better way of doing it.  While it still sends UN/PW with each header, it send it encrypted.  It does slow things down quite a bit.

I did get AuthenNTLM to work, kind of.  It works with Firefox and Opera, but not IE (6 or 7).  I'm banging my head on the wall trying to figure this out since it HAS to work with IE.

I'm also working on getting mod_ntlm to work.  Apache reloads fine, my settings look good, but I'm having the same problem where IE 6 & 7 cannot authenticate.  Again, FF and Opera work great.

I have checked my IE settings.  I am set to "Prompt For UN/PW".

Last, but not least, since I'm doing a PHP web app, I could always redirect login to a HTTPS login page, then using open_ldap authenticate it myself.  I could keep a user logged in using either a cookie or a session with some sort of token.  This way, things stay speedy because I'm not waiting for an NT server to authenticate me for every request. 

Thanks,
jmflyer

---

### Post by frobroj on 2007-01-02
jmflyer - Sounds like you are quite knowledgeable about the different auth mechanisms. Would it be sufficient to simply enable SSL on the web server using the auth_ldap in order to encrypt the uname and pw? I have it in opperation(Only on my local admin lan) but would like to use it elsewhere without reconfiguring a new mode of authentication.

Thanks!
Jeff M

---

### Post by jmflyer on 2007-01-02
I don't really know that much, I've just been reading a bunch the last week :-)

But to answer your question, yes, running all your pages SSL would solve the issue.  That would by far be the easiest solution.  EXCEPT - in my world - because any web developer using this type of authentication would have access to the users password via variables (PHP would be $_SERVER['REMOVE_USER_PW']).  My IT Department would flip.

Another alternate I just learned about is Digest.  It will md5 your PW in the header.  Then you can use some LDAP thing to do the AUTH.  Maybe passing it to PHP and using OPEN_LDAP().

I really want to get NTLM or Kerberos authentication working because then IE users joined to the Active Directory wouldn't even be prompted for their UN/PW since IE passes it automatically for Intranets (depending on your settings).

I still can't get past the IE errors though.  ](*,)   If ANYBODY out there has any ideas, I would love to hear them!  Things I've tried:
-Adding the site explicitly as an Intranet site
-Resetting everything to defaults
-Changing timout values, etc on the server
-Try random settings in IE (hey, it's windows, sometimes that works)

Right now I'm using the AuthenNTLR Perl module.  Like I said, works great with Firefox and Opera.  IE BLOWS!

Thanks,
JMFlyer

---

### Post by jmflyer on 2007-01-06
Just an update on my above reply...

I never figured out WTH was wrong with the NTLM.  However, if I switch to a sandbox domain that I setup, it works.  But once I move to my corprate domain, it fails again - but only with IE6&7.  I've compared headers, and apache logs from IE and Firefox, and can't come up with a good answer other than IE sucks.

The only difference between the two domains is that my corp. network is long (for example: machinename.building.corp.compay.com).  I've seen some thread saying that this may be the problem, but then why does it work in evey other browser...

So instead, I'm using some client side vbscript/ActiveX to figure out what the current username, password, and domain are and store them as a cookie.  Everyone at work uses IE except me, so this shouldn't be a problem. Since this site doesn't need to be particularly secure, this will suite my needs.  But I hate myself for having to use active X.  I REALLY hate myself.

If somebody is interested in seeing my stupid work around, you can private message me.  It's not something that I'm proud of and want to post here.

-JMFlyer

---

### Post by maphew on 2007-01-11
An idea which occured to me a couple of days ago but have not had the chance to research feasibility and apply is to install Apache with SSI on a windows machine along with mod_proxy and have it funnel everything, including $REMOTE_USER, back to the real ubuntu website.  This would avoid having to go through the pain of setting up ubuntu with kerberos, assigning valid tickets and so on.

---

