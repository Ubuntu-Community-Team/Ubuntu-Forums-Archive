---
title: "Mediawiki/samba domain authentication"
date: 2008-08-25
forum: Server Platforms
---

### Post by eDRoaCH on 2008-08-25
I have done quite a bit of reading via searching here and googling over the past couple days, but I am still a bit unclear.

I currently have an old dell destop at work that is running mediawiki as a documentation server and has been quite a success. It has earned itself a 'real' server (Poweredge 2850) and I want to take this opportunity to improve it.

What I need is to have mediawiki authenticate against the AD domain (w2k3) so all employees have a login, and I would like to have the option of having shares that authenticate against AD as well that only certain users can access.

I have read [http://www.mediawiki.org/wiki/Extension:LDAP_Authentication/AD_Configuration_Examples](http://www.mediawiki.org/wiki/Extension:LDAP_Authentication/AD_Configuration_Examples) but am rather unsure what it would take to get the SSL working. Which brings me to likewise-open.

1. Will likewise open smooth the domain connection issues for mediawiki? (basically take care of the SSL for me)
2. how do users sudo? I have read a few posts of trouble with this. Whats more is I dont want everyone to be able to sudo, only me and maybe a few others. Will I be able to use local accounts? Do I need to enable the root account?
3. I also want to be able to share certain folders to certain people, this isnt a requirement at the outset but I want to plan for it now.
4. Any other tips you may have on this configuration. 

Appreciate any help, as this is a production system I am really hoping for solid answers. Unfortunately I do not have the luxury of having a test system.

---

### Post by bab1 on 2008-08-26
If I get your drift;```
What I need is to have mediawiki authenticate against the AD domain (w2k3
```  You can use [[COLOR="Magenta"]LikeWise[/COLOR]]("https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html") or [[COLOR="Magenta"]WinBind[/COLOR]]("http://gentoo-wiki.com/HOWTO_Active_Directory_with_Samba_and_Winbind") to facilitate using AD user/passwords.  In other words the Ubuntu server becomes a member of the AD domain.

> ...(basically take care of the SSL for me)  SSL has nothing to do with AD integration.  Likewise enteprise might have SSL as a module.  I have no experience with that.  

> how do users sudo? I have read a few posts of trouble with this. Whats more is I don't want everyone to be able to sudo, only me and maybe a few others. Will I be able to use local accounts? Do I need to enable the root account?  The user has to be  in the "adm" group to be able to use sudo.  the fewer people that have full root privileges the better. Local accounts can be used as long as you have setup the login to search "files" when the AD search fails.  i did see that Likewise can manage sudoers.  That would be neat!

> I also want to be able to share certain folders to certain people...  Should not be a problem.

The only tip I can give you is to think out what you want to accomplish.  None of the questions mention what your overall goals are.  There may be alternatives...

---

### Post by eDRoaCH on 2008-08-26
I appreciate the help. The ultimate goal is to have mediawiki use domain accounts as its own accounts. This way I can cut it off to any non-authorized access.

That is 100% of what the server is used for right now, everything else is just icing. Of course I didn't want just anybody to be able to sudo either.

I have thrown together an old system I can do some testing on, but further pointers are welcome!

---

### Post by bab1 on 2008-08-26
So the reference to Samba was really for the windows users authentication.  If that is all, then both Winbind or Likewise will work.  Make sure that if you use Likewise that you test thoroughly.  I've read that it can be unstable.

---

### Post by flatline on 2008-08-26
I don't really have anything to add to this, but I am interested in a similar setup.  

In case anyone is unclear, basically what needs to happen is, Mediawiki will be configured so that only registered users can modify or even view the wiki.  The trick will be disabling the normal "create a user account" functionality, instead linking it to some other (AD in this case) domain.

---

### Post by bab1 on 2008-08-26
> The trick will be disabling the normal "create a user account" functionality, instead linking it to some other (AD in this case) domain.

I am not a Mediawiki person, but [**[COLOR="DarkGreen"]this[/COLOR]**]("The trick will be disabling the normal "create a user account" functionality, instead linking it to some other (AD in this case) domain.") looks promising.

---

### Post by eDRoaCH on 2008-09-04
Disabling access to non authenticated users is as easy as editing a line in the localsettings.php, though I cant find the exact link right now.

[http://www.mediawiki.org/wiki/Disable_account_creation](http://www.mediawiki.org/wiki/Disable_account_creation) should give you what you want on that.

Mediawiki has extensive and useful documentation, I am just having trouble understanding the info. How can I know if our AD is using SSL? I know MS password transactions are secure but I thought that was from Kerberos. 

The goal here is to authenticate mediawiki on AD (w2k3) domain user accounts. I was wondering if using likewise or similar would eliminate the SSL issues since on some level it would already be doing it, though maybe not the right way.

My IT guy threw a new issue my way today, he said to plan for w2k8 ^^;;;

Once again help appreciated. Has anyone accomplished authenticating mediawiki vs AD domains?

---

