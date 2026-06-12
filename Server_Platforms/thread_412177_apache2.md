---
title: "apache2"
date: 2007-04-17
forum: Server Platforms
---

### Post by tbuss on 2007-04-17
I have a question regarding apache2. Should I be placing the files of the site I want to display in :
*/usr/share/apache2/default-site*
or
*/var/www*

The reason I'm asking is because I was reading a thread on how to password protect my site and and it suggested I put the password file in a place it cannot be access from the outside.

Also, I'm a little confused by the way the How-To explains the steps.
> 
The directives discussed in this article will need to go either in your server configuration file (typically in a <Directory> section), or in per-directory configuration files (.htaccess files).

Should I be using the main server config file or is it better to use .htaccess files?
[B]
This is what I have:[/B]
```
<Directory /var/www//var/www/bussellExtended/>
AllowOverride AuthConfig
AuthType Basic
AuthName "Restricted FIles"
AuthUserFile /home/secure/apasswords
Require valid-user
</Directory>
```
This example looks like what I want, my question is, do I just add this to my apche config file? I'm not used to using config files and such. Or do I save this as a .htaccess file in the same dir as the files I'm trying to protect.

When looking in my config file I see entries such as *<Directory "/usr/share/apache2/icons">*
but like all the other entries they have a *Alias* line above them?

---

### Post by rmemm on 2007-04-17
My vote is /var/www for files as the default, though you can put them anywhere.

The "Directory" tags basically define access permissions to any directory in the file system so it can be anywhere.  The alias lines then map this directory into the URL name space.  The / for the URL name space is usually /var/www I think -- but check your setup.  So this means that anything under /var/www does not need an alias directive to map it into the url name space -- it should already be there -- though if you didn't like the url you could probably remap it.

If you want to add special protections to a directory -- you can use the directory tag and what it contains to modify protections just like your example.  If you want a secure directory -- there are aguments for not putting it in /var/www or under any other directory normally accessable though apache -- because for things you don't set -- permissions are inherited from the containing directories -- which means if you screw up a config -- a private sub directory can become visible if your not careful.

Regarding .htaccess files.  Your choice.  They are slower to access meaning on high volume sites -- it's best not to  use them -- but they are handy because apache does not have to be restarted to change options in them (unlike configs in /etc/apache2) - so for modifiable sites they can be better.  I've never used the .htaccess files myself -- so can't help you with the details.  However you do need to have them enabled in the main apache config files for them to work -- and they may or may not be setup that way by default.

Regarding your password file -- i'd probably protect it and put it in /etc somewhere such as /etc/apache2 directory for example.

Rob

---

### Post by tbuss on 2007-04-18
**Well, this is what I did:**
```
Directory /var/www/bussellExtended>
AllowOverride AuthConfig
AuthType Basic
AuthName "Family FIles"
AuthUserFile /home/secure/apasswords
require valid-user
</Directory>

```
**Then:**
restarted apache
```
sudo htpasswd -c /home/secure/apasswords family
set the password to "wtf"
sudo chown www-data:www-data /home/secure/apasswords
sudo chmod 0660 /home.secure/apasswords
sudo /etc/init.d/apache2 restart
```

**This is what's happening.**
When I navigate to the site in my browser, I'm prompted with the dialog box for unsername and password. However, if I click [COLOR="Red"]Cancel[/COLOR] three times without typing in the username and password, the page loads without any css support? If I click [COLOR="Red"]Close[/COLOR] without typing in a username and password, same result. If I click [COLOR="Red"]OK [/COLOR]three times without typing in a username and password, it just loads an empty page. 

Also, my htpasswd file contains the entry family:/mQstQkadCZ.o But I'm able to login with either family/mQstQkadCZ.o or family/wtf?

---

### Post by tbuss on 2007-04-18
**There is a slight typo in my post:**
*sudo chmod 0660 /home.secure/apasswords* 
**should be **
*sudo chmod 0660 /home/secure/apasswords*

---

### Post by rmemm on 2007-04-18
The password file is encrypted I think.  It should be whatever password you set.  Make certain you know what the case is of the password your using and the user name.

You general setup looks good to me.  

I assume you put all the files your protecting in the directory bussellExtended and that this directory exists in /var/www.  Also I'm assuming your DocumentRoot is /var/www.  May want to double check ownership and protections to make certain.

I don't know why a page is being shown without CSS -- that is if the page and css both are inside the /var/www/bussellExtended folder.  What page are you talking about?  What is the URL?

Other thing I don't remember is if order matters -- I'd put the inner directory defintions later in the config file than the outer ones.  I'm not sure this matters though.

Rob

---

### Post by tbuss on 2007-04-19
Okay, DocumentRoot is /var/www
I can login with the username:/password I created (family/wtf)
I can also login with the entry that is in my htpasswd (family:/mQstQkadCZ.o)
[INDENT][/INDENT]I can't figure out why the htpasswd file isn't family/wtf)'?
I apologize for adding the css problem, I know why this is happening, Like you siad; I have all the stylesheets located in another folder. But they loaded fine until this....
What I don't think makes sense, is the fact that I can login even though I don't autho; I can simply click cancel 3 times and /var/www/bussellExtended/index.html loads (without css)
I close out the dialog box (3 times) without ever auto, it loads /var/www/bussellExtended/index.html loads (without css)

I've tried changing Directory /var/www/bussellExtended>
to 
Directory /var/www>
But that just resulted in the password prompt going away all together

I was told to:
> try putting junk in your htaccess file. If it's being read, you will get an Internal Server Error when accessing that resource.
But I don't see how this will help since I'm able to get a login prompt, and login? But I looked for .htaccess and I could never find a file for apache2, I think I got something seriously mis configured or not  configured at all

---

### Post by rmemm on 2007-04-20
Seems strange to me also.

What it sounded like to me was that your password is protecting the CSS file and perhaps other things the document references and your not password protecting the document itself.  Since you get 3 prompts -- perhaps -- your page your loading referencs 3 such protected content objects.  That's what the result suggests -- why this is -- seems like something in your setup in the config files somewhere in /etc/apache2 -- but as you said, really strange.

How about going back to basics a little.  I was very confused myself when first setting up the files in /etc/apache2 -- and still have to think about it.  I believe how this works is that the main config files starts in apache2.conf -- but it includes a lot of other files.  One approach is to start there and scan through it and all of the sub-files -- tough maybe that's excessive.  Why I mention the apache2.conf file is a lot of the basic site policies are set there and so it's at least looking at that one file.

The other thing -- are you setting up your site using the virtual host files in sites-enabled? Normally what people do I think is either edit the "default" version of that or add on of their own and used the a2ensite command to enable the new site -- and perhaps use a2dissite to disable the default.  I mention this because maybe your config is either not really enabled by a2ensite or maybe something in "default" is causing you problems.

Other thing you could try is to move your protected directory out of /var/www and then use a directory directective to setup access and an alias directive to map it to the URL name space.  The advantage of this is that for the most part -- you want won't inherit andy of the permissiosn from the /var/www tree -- meaning if there's some setting that's causing you problems it may cease to be a problem.  Also you might want to search for all "directory" directivies in the /etc/apache2 files and see what they are -- especially if there are any ones that don't reference a directory name -- these effect the global defaults for all directories.  A hint you can search with grep -nri "directory" /etc/apache2.

The other thing you sometimes have to consider is do you have the correct modules enabled.  The a2enmod and a2dismod commands enable and disable these.  I think probably you have all of the modules you need -- but I'm just mentioning this in passing.

The other thing I would think through is your directory and url name space setup.  As I said before it sounds like your main document is not protected for some reason and 3 things it references are protected perhaps.  It's probably worth thinking through that all of you files you referencing and using are where you think they are -- and that these are in facted mapped into the URL space like you think they are -- and that your using the correct URLs for them.  I just mention this because this is somewhat complicated -- and I'm not certain how much experience you have with this sort of thing.

Sorry no solution -- just trying to spark an idea.  Maybe something I said will help.

Rob

---

### Post by rmemm on 2007-04-20
By the way -- in the previous post I meant "sites-available" not sites "sites-enabled".  The way apache works is you setup sites in "sites-available" and enable them to get a link put into "sites-enabled".

Rob

---

### Post by tbuss on 2007-04-20
I've made progress, but what one problem still remains

**I changed:**

*Directory /var/www/bussellExtended>*

**to**

*<Directory /var/www/>*

When I connect with the site, a login prompt appears and** I'm not** allowed to bypass the login by clicking cancel or closing out the box. Good (and all stylesheets load as advertised)

But, the problem now lies with the password I use for the login. As I mentioned earlier I set the password by using these steps:

*sudo htpasswd -c /home/secure/apasswords family*
**set encryptedpassword**
[I]sudo chown www-data:www-data /home/secure/apasswords
sudo chmod 0660 /home/secure/apasswords[/I]

The password I'm using is the one I declared in those steps, it works and I'm allowed entry into the site.
However, when I checked the /home/secure/apasswords file the entry is not what I'm using it is this:
*family:/mQstQkadCZ.o*

So there are two questions that are puzzling me:
1. Why is there an entry in my /home/secure/apasswords that is family:/mQstQkadCZ.o instead of family:/encryptedpassword
2. And where is the file that has the entry for the password that I'm using?

---

### Post by rmemm on 2007-04-20
I'm assuming that the password your seeing is the "crypt" encrypted password.  If you want md5 encrypted passowords use the -m option.  Do I understand your question or am I missing something?  As far as I know crypt is the default encryption for Linux.

Rob

---

### Post by rmemm on 2007-04-20
If I wasn't clear -- I'm personally not suprised at what your password file looks like because what would normally happen is that when htpasswd adds a user name and password entry it will add the user name as is -- then use the crypt encryption algorithm (or optionally the md5 algorithm) to create an encrpyted version of that -- it it should save that in the password file. Then when you enter a password -- apache does the same thing and compares the encrypted or actually it's called the "hashed" value to the original "hashed" value.

Does that make any sense?

Rob

---

### Post by tbuss on 2007-04-20
memm,

no man, I'm an idiot. I got so bent around the axel that they didn't match, not realizing that the contents are encrypted. I don't know what I was thinking. I have to get used to the fact that in linux; things work, and not to anticipate a error like I always did in windows. I apologize man, I know you were trying to help and your post were very informative. Next time I won't be so eager to run to the forums without first reasearching, or thinking.

Thanks again for your help

---

