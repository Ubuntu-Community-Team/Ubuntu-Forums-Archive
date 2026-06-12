---
title: "Ubuntu and Original Xbox"
date: 2011-10-20
forum: The Cafe
---

### Post by thig1002 on 2011-10-20
**I'm going to describe a detailed scenario, and I would like to know if it could be a possibility: **
 
I have an original Virgin Xbox. Anyone who is into gaming (or doesn't live under a rock) understands that the Original Xbox has no value as strictly a gaming consol. I would like to install a version of Ubuntu on to my Xbox, preferrably without hard modding... 
 
Exploiting an Xbox is the easy part, but my question is could Ubuntu/Kubuntu/Xubuntu be installed on its hardrive? If so, how?
 
As far as system specs are concerned, what would work the best? 
 
**To put it simply, I want to turn my little black box into a linux computer.**

---

### Post by MonolithImmortal on 2011-10-20
[http://www.xbmc4xbox.org/about](http://www.xbmc4xbox.org/about)

---

### Post by Spice Weasel on 2011-10-20
Running unofficial binaries on the Xbox is questionably legal... Besides, the black Xbox only has a 733MHz Intel Mobile Celeron processor, a 10 GB hard drive and 64MB of RAM so it's pretty pointless unless you enjoy only using CLI.

---

### Post by KiwiNZ on 2011-10-20
An huge amount of hassle and work for very little return. Like climbing the Matterhorn to get a Egg cup of Beer placed on the summit.

---

### Post by dniMretsaM on 2011-10-20
> **Spice Weasel said:**
> Running unofficial binaries on the Xbox is questionably legal... Besides, the black Xbox only has a 733MHz Intel Mobile Celeron processor, a 10 GB hard drive and 64MB of RAM so it's pretty pointless unless you enjoy only using CLI.

He could stick SliTaz or ChrunchBang or something on there.

> **KiwiNZ said:**
> An huge amount of hassle and work for very little  return. Like climbing the Matterhorn to get a Egg cup of Beer placed on  the summit.

It might be a fun project, though. I know I'd enjoy something like that even if it didn't work spectacularly.

---

### Post by Spice Weasel on 2011-10-20
> **dniMretsaM said:**
> He could stick SliTaz or ChrunchBang or something on there.

Nope. They would have to use the Xbox kernel fork-type thing to be compatible, and they don't. [Distributions that are compatible]("http://sourceforge.net/projects/xbox-linux/files/") with the Xbox are GentooX, xUbuntu (not Xubuntu, very slow), X-DSL (horribly outdated), Xebian Sarge (horribly outdated, only useful as a server) and Fedora (broken). 

The only legal way to install Linux on an Xbox is to replace the BIOS with Cromwell, but it's risky and will render it unable to play Xbox games. So if you mess up, you won't have a second chance because you won't be able to load the MechAssault disc to replace the BIOS.

---

### Post by dniMretsaM on 2011-10-20
> **Spice Weasel said:**
> Nope. They would have to use the Xbox kernel fork-type thing to be compatible, and they don't. [Distributions that are compatible]("http://sourceforge.net/projects/xbox-linux/files/") with the Xbox are GentooX, xUbuntu (not Xubuntu, very slow), X-DSL (horribly outdated), Xebian Sarge (horribly outdated, only useful as a server) and Fedora (broken). 

The only legal way to install Linux on an Xbox is to replace the BIOS with Cromwell, but it's risky and will render it unable to play Xbox games. So if you mess up, you won't have a second chance because you won't be able to load the MechAssault disc to replace the BIOS.

Ah ok. Well, I guess it's up to him if he wants to risk it.

---

### Post by Stigmata13 on 2011-10-20
While it is possible to run a custom linux distro on the original xbox, it isn't very pretty as you have to order adapters or even make custom adapters just to be able to use a mouse and keyboard and such.

My advice is to try xbmc (xbox media center) on the xbox, there is a method of soft-modding the xbox or you can get a mod chip, but I'm not going into that as it isn't exactly legal. Google is your friend.

---

### Post by thig1002 on 2011-10-31
This is all very helpful...

And really this is just a side project/I'm bored out of my mind/How many different ways can I kill my xbox... Thing.
 
Using it as a server sounds like a decent idea, but upgrading the memory seems like a needed task for that.

The reason I was asking about Ubuntu is because it comes preloaded with drivers for xbox/xbox360 controllers, so it seemed to be the best option. Obviously not "Ubuntu" per say, but maybe xubuntu.
 
So it sounds to me like the only way it would actually be a functional project is to upgrade the memory and turn it into a server?

---

### Post by daithi23 on 2012-08-03
Hi, I was looking to set up a server for use with Ushahidi and the only thing I have to hand is an old Xbox. I would have liked to use Ubuntu as I'm (a bit) familiar with it but that doesn't look like the right option.
I know the only legal way to do it is to replace the BIOS with Cromwell which I'm fine with as it won't be able to play games anymore.
Any suggestions for a distro to put on? Ushahidi's website has these requirements for installing the platform:

> This section outlines the requirements for installing the Ushahidi platform on your computer.
   **The "AMP" (Apache, Mysql, PHP) Stack**

  Before installing Ushahidi, following must be installed in the target system:
  
[LIST]
[*]PHP version 5.2.3 or greater
[*]MySQL version 5.0 or greater
[*]An HTTP Server. Kohana, which Ushahidi is built on, is known to work with the following web servers:
[LIST]
[*]Apache 1.3+
[*]Apache2.0+
[*]lighttpd
[*]Microsoft Internet Information Server (MS IIS)
[*]Nginx
[/LIST]
     
[*]Unicode support in the operating system
[/LIST]
   **Required PHP Extensions**

  The follwing is a list of PHP extensions that must be installed on your server in order for Ushahidi to run properly:
 
[LIST]
[*]PCRE ([http://php.net/pcre](http://php.net/pcre)) must be compiled with --enable-utf8 and --enable-unicode-properties for UTF-8 functions to work properly.
[*]iconv ([http://php.net/iconv](http://php.net/iconv)) is required for UTF-8 transliteration.
[*]mcrypt ([http://php.net/mcrypt](http://php.net/mcrypt)) is required for encryption.
[*]SPL ([http://php.net/spl](http://php.net/spl)) is required for several core libraries
[*]mbstring ([http://php.net/mbstring](http://php.net/mbstring)) which speeds up Kohana's UTF-8 functions.
[*]cURL ([http://php.net/curl](http://php.net/curl)) which is used to access remote sites.
[*]MySQL ([http://php.net/mysql](http://php.net/mysql)) is required for database access.
[/LIST]
   **NOTE: Need to figure out what extensions you already have installed on your server? Here are instructions to do just that: ****[http://jontangerine.com/silo/php/phpinfo/](http://jontangerine.com/silo/php/phpinfo/)**
  **Optional Server Requirements**

  
[LIST]
[*]To use Ushahidi's "Clean URLS" feature on an Apache Web Server, you  will need the mod_rewrite module and the ability to use local .htaccess  files. To check if local .htaccess files are allowed, verify that the  "AllowOverride" directive in your Apache config (for the web server  directory in which you have installed Ushahidi) has been set to "All"  i.e.:
[/LIST]
    <Directory [your-document-root-directory]>     ...     AllowOverride All     ... </Directory>  

  **NOTE: Clean URLs means that the URLs of your deployment will not have the 'index.php' prefix**


---

### Post by Primefalcon on 2012-08-03
Ubuntu should be able to run... I have 10.04 lubuntu running a machine with a lot lower specs (about a 200mhz processor)...

you could also run puppy linux

---

