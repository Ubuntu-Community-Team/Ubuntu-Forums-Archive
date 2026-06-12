---
title: "Failed install.."
date: 2009-07-27
forum: Ubuntuzilla
---

### Post by petejk on 2009-07-27
Hi, 
I cant seem to be able to successfully run the ubuntuzilla script and install firefox 3.5.1.
My output is below:
Thanks, 


root@Laptop1:/home/petejk# ubuntuzilla.py -g
^[[5~
Welcome to the Ubuntuzilla Firefox script version 4.6.3

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.1. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. as           3. be        
  4. bg           5. bn-BD        6. bn-IN        7. ca        
  8. cs           9. cy          10. da          11. de        
 12. el          13. en-GB       14. en-US       15. eo        
 16. es-AR       17. es-CL       18. es-ES       19. es-MX     
 20. et          21. eu          22. fa          23. fi        
 24. fr          25. fy-NL       26. ga-IE       27. gl        
 28. gu-IN       29. he          30. hi-IN       31. hr        
 32. hu          33. id          34. is          35. it        
 36. ja          37. ka          38. kk          39. kn        
 40. ko          41. ku          42. lt          43. lv        
 44. mk          45. ml          46. mn          47. mr        
 48. nb-NO       49. nl          50. nn-NO       51. oc        
 52. or          53. pa-IN       54. pl          55. pt-BR     
 56. pt-PT       57. rm          58. ro          59. ru        
 60. si          61. sk          62. sl          63. sq        
 64. sr          65. sv-SE       66. ta-LK       67. ta        
 68. te          69. th          70. tr          71. uk        
 72. vi          73. zh-CN       74. zh-TW     
Enter your choice of localization (integer, from 0 to 74): 13
You have chosen localization en-GB. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Old firefox preferences not found. Nothing to back up. Proceeding with installation.

Retrieving package name for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/) | grep 'firefox' | grep -v '\.asc' |grep -v 'ftp://' | awk '{ print substr($0,index($0, "firefox"))}' | awk '{print $1}' | sed -e 's/\.*$//'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/.\n"]
Download error. Trying again, hoping for a different mirror.
Success!: firefox-3.5.1.tar.bz2

Downloading Firefox archive from the Mozilla site

--2009-07-28 00:09:29--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/firefox-3.5.1.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB/firefox-3.5.1.tar.bz2)
           => `firefox-3.5.1.tar.bz2'
Resolving releases.mozilla.org... 204.152.184.113, 204.152.184.196, 204.246.0.136, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-GB ... done.
==> SIZE firefox-3.5.1.tar.bz2 ... 9650907
==> PASV ... done.    ==> REST 9650907 ... done.    
==> RETR firefox-3.5.1.tar.bz2 ... done.
Length: 9650907 (9.2M), 0 (0) remaining

100%[+++++++++++++++++++++++++++++++++++++++] 9,650,907   --.-K/s   in 0s      

2009-07-28 00:09:32 (0.00 B/s) - `firefox-3.5.1.tar.bz2' saved [9650907]


bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: Broken pipe
    Input file = (stdin), output file = (stdout)
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
sudo tar -C /opt -xjf firefox-3.5.1.tar.bz2
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1225, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 283, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 310, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 683, in install
    self.extractArchive()
  File "/usr/local/bin/ubuntuzilla.py", line 564, in extractArchive
    self.util.execSystemCommand(executionstring="sudo tar -C " + self.options.targetdir + " " + self.tar_flags + " " + self.packageFilename)
  File "/usr/local/bin/ubuntuzilla.py", line 145, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by graaant on 2009-07-27
I get the same here :(

---

### Post by wojox on 2009-07-27
Just download it from here:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by graaant on 2009-07-27
Won't that leave us with firefox and shiretoko?

---

### Post by nanotube on 2009-07-27
huh, weird... haven't seen that happening - does that persist with multiple retries?

also, try the latest ubuntuzilla (4.7.0) and see if that helps
haven't made any changes to this piece, but just in case. :)

---

### Post by graaant on 2009-07-27
It's happening every time.
Using 4.7.0 - Kubuntu 9.04 and Ubuntu 9.10 are having the same error.

---

### Post by nanotube on 2009-07-28
> **graaant said:**
> It's happening every time.
Using 4.7.0 - Kubuntu 9.04 and Ubuntu 9.10 are having the same error.

is it possible that your download is getting corrupted? is the gpg signature check passing?

---

### Post by graaant on 2009-07-28
> **nanotube said:**
> is it possible that your download is getting corrupted? is the gpg signature check passing?

Doesn't seem to be getting that far, my last run shows this:

```
grant@converge:~$ ubuntuzilla.py                                               

Welcome to the Ubuntuzilla Firefox script version 4.7.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)                                             

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/

Retrieving the version of the latest release of Firefox from the Mozilla website...
wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com |grep 'product=' -m 1
Failed to retrieve the latest version of Firefox
Process returned code 1
[]
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1254, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 281, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 308, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 697, in install
    self.getLatestVersion()
  File "/usr/local/bin/ubuntuzilla.py", line 857, in getLatestVersion
    self.releaseVersion = self.util.getSystemOutput(executionstring="wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com |grep 'product=' -m 1", numlines=1, errormessage="Failed to retrieve the latest version of "+ self.options.package.capitalize())
  File "/usr/local/bin/ubuntuzilla.py", line 121, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
grant@converge:~$

```

Seems to get further every now and then, can download the package, I see it go that far. Abvoe you can see that it didn't even get to the localization step.

---

### Post by petejk on 2009-07-28
Well, sorted problem now!
I downloaded firefox-3.5.1.tar.bz2 from [http://www.mozilla.com/en-US/firefox/3.5.1/releasenotes/](http://www.mozilla.com/en-US/firefox/3.5.1/releasenotes/) , which saved to my desktop

Opened terminal, ran 'sudo nautilus' , and dragged a copy of firefox-3.5.1.tar.bz2 to my tmp folder (if there's a file by the same name in there already, replace it).

ubuntuzilla.py -g now executed successfully! Must have been a permissions issue..

---

### Post by graaant on 2009-07-28
That didn't work for me.
Still bails out, at a seemingly random time, same error every time :(

---

### Post by nanotube on 2009-07-28
> **petejk said:**
> Well, sorted problem now!
I downloaded firefox-3.5.1.tar.bz2 from [http://www.mozilla.com/en-US/firefox/3.5.1/releasenotes/](http://www.mozilla.com/en-US/firefox/3.5.1/releasenotes/) , which saved to my desktop

Opened terminal, ran 'sudo nautilus' , and dragged a copy of firefox-3.5.1.tar.bz2 to my tmp folder (if there's a file by the same name in there already, replace it).

ubuntuzilla.py -g now executed successfully! Must have been a permissions issue..

hi
first, there's no reason to be root to write to /tmp - just for next time :)
second, is there a reason you run it with -g in the first place? checking gpg signature is an important archive integrity verification step...

---

### Post by nanotube on 2009-07-28
> **graaant said:**
> That didn't work for me.
Still bails out, at a seemingly random time, same error every time :(

is your network connection otherwise ok? if it bails at random times, seems like network irregularities to me...

---

### Post by graaant on 2009-07-30
> **nanotube said:**
> is your network connection otherwise ok? if it bails at random times, seems like network irregularities to me...

Network connection is fine and stable.
I'm beggining to think this might have something to do with the python upgrades in Karmic?

---

### Post by nanotube on 2009-07-31
> **graaant said:**
> Network connection is fine and stable.
I'm beggining to think this might have something to do with the python upgrades in Karmic?

hmm, don't know - i still run intrepid.
if it is something to do with python, you could try running with "python2.5" instead of just "python". so, try something like:
```
python2.5 /usr/local/bin/ubuntuzilla.py
```
and see if it's any different...

---

### Post by graaant on 2009-08-02
Specifying python2.5 didn't seem to help.
It spits the same errors every time, <module>, <start>, etc.
I can't work out why though :(

```
gashman@grant-laptop:~$ python2.5 /usr/local/bin/ubuntuzilla.py 

Welcome to the Ubuntuzilla Firefox script version 4.7.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Firefox from the Mozilla website...
wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com |grep 'product=' -m 1
Failed to retrieve the latest version of Firefox
Process returned code 1
[]
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1254, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 281, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 308, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 697, in install
    self.getLatestVersion()
  File "/usr/local/bin/ubuntuzilla.py", line 857, in getLatestVersion
    self.releaseVersion = self.util.getSystemOutput(executionstring="wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com |grep 'product=' -m 1", numlines=1, errormessage="Failed to retrieve the latest version of "+ self.options.package.capitalize())
  File "/usr/local/bin/ubuntuzilla.py", line 121, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
gashman@grant-laptop:~$ 

```

---

### Post by nanotube on 2009-08-03
weird...
maybe mozilla's site is doing something weird because you're coming from australia...

could you post the complete output of 
```

wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com

```

by the way, if you just want to get mozilla build running and don't care about automatic update notifications and other extra frills of ubuntuzilla, you could try using this method of install:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by graaant on 2009-08-03
Here's the output. Not sure if this is what I should be expecting. :S

```
gashman@grant-laptop:~$ wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en-US" lang="en-US" dir="ltr">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    <title>Mozilla | Firefox web browser &amp; Thunderbird email client</title>
    <script type="text/javascript" src="/js/util.js"></script>
    <link rel="stylesheet" type="text/css" href="/includes/yui/2.5.1/reset-fonts-grids/reset-fonts-grids.css" />
    <link rel="stylesheet" type="text/css" href="/includes/yui/2.5.1/menu/assets/skins/sam/menu.css" />
    <link rel="stylesheet" type="text/css" href="/style/tignish/template.css" media="screen" />
    <link rel="stylesheet" type="text/css" href="/style/tignish/content.css" media="screen" />
    <script type="text/javascript" src="/includes/yui/2.5.1/yahoo-dom-event/yahoo-dom-event.js"></script>
    <script type="text/javascript" src="/includes/yui/2.5.1/container/container_core-min.js"></script>
    <script type="text/javascript" src="/includes/yui/2.5.1/menu/menu-min.js"></script>
    <script type="text/javascript" src="/js/mozilla-menu.js"></script>
        <meta name="keywords" content="Firefox, Mozilla Firefox, Mozilla, Thunderbird, Thunderbird 2, Thunderbird email, email, Firefox 2, Foxfire, Fire Fox, browser, web browser, internet browser, web, pop-up blocker, internet, speed, secure, customize, online, add-ons, fastest, download Firefox" />
    <meta name="description" content="Mozilla is a global community dedicated to building free, open source products like the award winning Firefox web browser and Thunderbird email software." />
    <link rel="stylesheet" type="text/css" href="/style/tignish/home.css" media="screen" />
    <!--[if lt IE 7.]>
    <script defer type="text/javascript" src="/js/pngfix.js"></script>
    <![endif]-->
</head>

<body id="home" class="">

<!-- SiteCatalyst Reporting -->
<script type="text/javascript">s_account="mozillacom";</script>
<script src="/js/s_code.js" type="text/javascript"></script>
<script type="text/javascript">// <![CDATA[
// add classes to body to indicate browser version and JavaScript availabiliy
if (document.body.className == '') {
    document.body.className = 'js';
} else {
    document.body.className += ' js';
}

if (gPlatform == 1) {
    document.body.className += ' platform-windows';
} else if (gPlatform == 3 || gPlatform == 4) {
    document.body.className += ' platform-mac';
} else if (gPlatform == 2) {
    document.body.className += ' platform-linux';
}

// ]]></script>

<div id="breadcrumbs">
    
</div>

<noscript><div id="no-js-feature"></div></noscript>

<div id="wrapper">
<div id="doc">

    <div id="nav-access">
        <a href="#nav-main">skip to navigation</a>
        <a href="#lang_form">switch language</a>
    </div>

    <!-- start #header -->
    <div id="header">
        <div>
        <h1><a href="/en-US/" title="Back to home page"><img src="/img/tignish/template/mozilla-logo.png" height="56" width="145" alt="Mozilla" /></a></h1>
        
<!-- start #nav-main -->
<div id="nav-main" class="yuimenubar yuimenubarnav">
  <div class="bd">
    <ul class="first-of-type">
<li id="menu_products" class="yuimenubaritem"><a href="/en-US/products/">Products</a>
      <div class="yuimenu">
        <div class="bd">
          <ul>
<li id="submenu_firefox" class="yuimenuitem"><a href="/en-US/products/firefox/">Firefox</a></li><li id="submenu_thunderbird" class="yuimenuitem"><a href="/en-US/products/thunderbird/">Thunderbird</a></li></ul>
        </div>
      </div>
      </li><li id="menu_addons" class="yuimenubaritem"><a href="https://addons.mozilla.org/">Add-ons</a>
      <div class="yuimenu">
        <div class="bd">
          <ul>
<li id="submenu_addons_all" class="yuimenuitem"><a href="https://addons.mozilla.org/firefox/">All Add-ons</a></li><li id="submenu_addons_recommended" class="yuimenuitem"><a href="https://addons.mozilla.org/firefox/recommended">Recommended</a></li><li id="submenu_addons_popular" class="yuimenuitem"><a href="https://addons.mozilla.org/firefox/browse/type:1/cat:all?sort=popular">Popular</a></li><li id="submenu_addons_themes" class="yuimenuitem"><a href="https://addons.mozilla.org/firefox/browse/type:2">Themes</a></li><li id="submenu_addons_search" class="yuimenuitem"><a href="https://addons.mozilla.org/firefox/browse/type:4">Search Engines</a></li><li id="submenu_addons_plugins" class="yuimenuitem"><a href="https://addons.mozilla.org/firefox/browse/type:7">Plugins</a></li></ul>
        </div>
      </div>
      </li><li id="menu_support" class="yuimenubaritem"><a href="http://support.mozilla.com/">Support</a>
      <div class="yuimenu">
        <div class="bd">
          <ul>
<li id="submenu_support_kb" class="yuimenuitem"><a href="http://support.mozilla.com/en-US/kb/">Firefox Support</a></li><li id="submenu_support_thunderbird" class="yuimenuitem"><a href="http://www.mozilla.org/support/thunderbird/">Thunderbird Support</a></li></ul>
        </div>
      </div>
      </li><li id="menu_community" class="yuimenubaritem"><a href="/en-US/manyfaces/">Community</a>
      <div class="yuimenu">
        <div class="bd">
          <ul>
<li id="submenu_community_addons" class="yuimenuitem"><a href="http://addons.mozilla.org/">Add-ons</a></li><li id="submenu_community_bugzilla" class="yuimenuitem"><a href="https://bugzilla.mozilla.org/">Bugzilla</a></li><li id="submenu_community_devmo" class="yuimenuitem"><a href="http://developer.mozilla.org/">Mozilla Developer Center</a></li><li id="submenu_community_labs" class="yuimenuitem"><a href="http://labs.mozilla.com/">Mozilla Labs</a></li><li id="submenu_community_mozillamessaging" class="yuimenuitem"><a href="http://www.mozillamessaging.com/">Mozilla Messaging</a></li><li id="submenu_community_mozillaorg" class="yuimenuitem"><a href="http://www.mozilla.org/">Mozilla.org</a></li><li id="submenu_community_mozillazine" class="yuimenuitem"><a href="http://www.mozillazine.org/">MozillaZine</a></li><li id="submenu_community_planet" class="yuimenuitem"><a href="http://planet.mozilla.org/">Planet Mozilla</a></li><li id="submenu_community_qmo" class="yuimenuitem"><a href="http://quality.mozilla.org/">QMO</a></li><li id="submenu_community_spreadfirefox" class="yuimenuitem"><a href="http://www.spreadfirefox.com/">Spread Firefox</a></li><li id="submenu_community_support" class="yuimenuitem"><a href="http://support.mozilla.com/">Support</a></li></ul>
        </div>
      </div>
      </li><li id="menu_aboutus" class="yuimenubaritem"><a href="/en-US/about/">About</a>
      <div class="yuimenu">
        <div class="bd">
          <ul>
<li id="submenu_about" class="yuimenuitem"><a href="/en-US/about/whatismozilla.html">What is Mozilla?</a></li><li id="submenu_getinvolved" class="yuimenuitem"><a href="/en-US/about/get-involved.html">Get Involved</a></li><li id="submenu_press" class="yuimenuitem"><a href="/en-US/press/">Press Center</a></li><li id="submenu_careers" class="yuimenuitem"><a href="/en-US/about/careers.html">Careers</a></li><li id="submenu_partnerships" class="yuimenuitem"><a href="/en-US/about/partnerships.html">Partnerships</a></li><li id="submenu_licensing" class="yuimenuitem"><a href="http://www.mozilla.org/foundation/licensing.html">Licensing</a></li><li id="submenu_blog" class="yuimenuitem"><a href="http://blog.mozilla.com/">Blog</a></li><li id="submenu_store" class="yuimenuitem"><a href="http://store.mozilla.org/">Store</a></li><li id="submenu_community_store" class="yuimenuitem"><a href="http://communitystore.mozilla.org/">Community Store</a></li><li id="submenu_logo" class="yuimenuitem"><a href="/en-US/about/logo/">Logo Guide</a></li><li id="submenu_contact" class="yuimenuitem"><a href="/en-US/about/contact.html">Contact Us</a></li></ul>
        </div>
      </div>
      </li></ul>
  </div>
</div>
<!-- end #nav-main -->

        <form id="moz_global_search" action="/en-US/search/" method="get"><div>
            <input type="hidden" name="hits_per_page" id="hits_per_page" value="" />
            <input type="hidden" name="hits_per_site" id="hits_per_site" value="" />
            <input type="text" name="query" id="query" value="" /><input type="image" src="/img/tignish/content/search-button.png" id="submit" alt="Search" />
        </div></form>
        </div>
    </div>
    <!-- end #header -->

    <hr class="hide" />

<script type="text/javascript">// <![CDATA[
    // Add a class to the body tag to alternate background features
    var class_options = new Array( "variation1", "variation2", "variation3, variation4" );

    if (Math.random) {
        var choice = Math.floor(Math.random() * (class_options.length));

        // Just in case javascript gets carried away...
        choice = ( (choice < class_options.length)  && choice >= 0) ? choice : 0;

        if (document.body.className == '') {
            document.body.className = class_options[choice];
        } else {
            document.body.className += ' '+class_options[choice];
        }
    }
// ]]></script>
<div id="main-feature">
    <div id="feature-contents">
    <h2><a href="firefox/"><img src="/img/tignish/home/feature-logo.png" alt="Firefox 3.5" width="400" height="105" id="primary-logo" /></a></h2>
    <p>Browse in the fast lane: upgrade to the fastest, safest and smartest Firefox yet. <a href="/en-US/firefox/">Learn&nbsp;more.</a></p>
    </div>
    <script type="text/javascript" src="/js/download.old.js"></script>
    <script type="text/javascript">
        <!--
        // Configure the Firefox download write script

        var gDownloadItemTemplate = " <li class=\"%CSS_CLASS%\"> <a onclick=\"javascript:do_download('%BOUNCER_URL%'); urchinTracker('\/firefox\/download\/0706abtest\/?control');\" href=\"%DOWNLOAD_URL%\" class=\"download-link download-firefox\"> <span><strong>Download Firefox - Free<\/strong> <em>%VERSION% for %PLATFORM_NAME%</em> <em class=\"download-lang\">%LANGUAGE_NAME%&nbsp;(%FILE_SIZE%)<\/em><\/span><\/a> <\/li>";
        // Temporary fix for bug 439792
        if (gPlatform == PLATFORM_MACOSX) {
            gDownloadItemTemplate = " <li class=\"%CSS_CLASS%\"> <a onclick=\"javascript:do_download('%BOUNCER_URL%'); urchinTracker('\/firefox\/download\/0706abtest\/?control');\" href=\"%DOWNLOAD_URL%\" class=\"download-link download-firefox\"> <span><strong>Download Firefox - Free<\/strong> <em>%VERSION% for %PLATFORM_NAME% 10.4 and above</em> <em class=\"download-lang\">%LANGUAGE_NAME%&nbsp;(%FILE_SIZE%)<\/em><\/span><\/a> <\/li>";
        }
        var gDownloadItemMacOS9 = "<a href=\"\">MacOS 9 and earlier are not supported<\/a>";
        var gDownloadItemOtherPlatform = "<a href=\"/en-US/firefox/3.5.2/releasenotes/#contributedbuilds\">Free Download<\/a>"

        document.writeln("<ul class=\"home-download " + gCssClass + " \">");
        writeDownloadItems("fx");
        document.writeln("<\/ul>");
        document.writeln("<div class=\"download-other\"><span class=\"other\">");
        document.writeln("<a href=\"\/en-US\/firefox\/3.5.2\/releasenotes\/\">Release Notes<\/a>");
        document.writeln("- <a href=\"\/en-US\/firefox\/all.html\">Other Systems and Languages<\/a>");
        document.writeln("<\/span><\/div>");
        //-->
    </script>
    
            <noscript>
                <div class="download download-noscript">
                <h3>Download Now - Free <span>(English (US) | <a href="http://www.mozilla.com/en-US/firefox/all.html">Other Systems and Languages</a>)</span></h3>
                <ul>
                                    <li><a href="http://download.mozilla.org/?product=firefox-3.5.2&amp;os=win&amp;lang=en-US">Windows (7.7<abbr title="MegaBytes">MB</abbr>)</a></li>
                                    <li><a href="http://download.mozilla.org/?product=firefox-3.5.2&amp;os=linux&amp;lang=en-US">Linux (9.4<abbr title="MegaBytes">MB</abbr>)</a></li>
                                    <li><a href="http://download.mozilla.org/?product=firefox-3.5.2&amp;os=osx&amp;lang=en-US">Mac OS X (17.6<abbr title="MegaBytes">MB</abbr>)</a></li>
                </ul>
                </div>
            </noscript></div>

<hr class="hide" />

<div id="main-content">

    <h3>What’s Happening at Mozilla?</h3>
    <dl class="news">
        <dt><a href="/en-US/press/mozilla-2009-06-30.html">Mozilla Advances the Web with Firefox 3.5</a></dt>
        <dd>Includes upgrades to performance, features, Web standards support and more.</dd>
        <dt><a href="http://blog.mozilla.com/blog/2009/07/08/mozilla-introduces-harry-potter-personas/">Introducing Harry Potter Personas</a></dt>
        <dd>Decorate your Firefox with art from <em>Harry Potter and the Half Blood Prince</em>.</dd>
        <dt><a href="http://blog.mozilla.com/blog/2009/07/22/fastest-firefox-the-mozilla-community-shows-its-speed/">The Mozilla Community Shows Its Speed</a></dt>
        <dd>Fasten your seat belt and watch the final video in our Fastest Firefox series.</dd>
        <dt><a href="http://blog.mozilla.com/blog/2009/06/15/be-the-difference-mozilla-service-week/">Be the Difference: Mozilla Service Week</a></dt>
        <dd>Find out how you can use the Web to help your community.</dd>
    </dl>

</div>

<div id="sidebar">
    <div class="front-feature" id="thunderbird-feature">
        <h3><a href="/en-US/thunderbird/">Thunderbird</a></h3>
        <p><a href="/en-US/thunderbird/">Enjoy safe, fast, and easy email, Mozilla-style.</a></p>
    </div>
    <div class="front-feature" id="store-feature">
        <h3><a href="http://store.mozilla.com" class="external"><span>Mozilla Gear</span></a></h3>
        <p>Shop the <a href="http://store.mozilla.com" class="external">Mozilla Store</a> and <a href="http://communitystore.mozilla.org" class="external">Community Store.</a></p>
    </div>
    <div class="front-feature" id="hiring-feature">
        <h3><a href="/en-US/about/careers.html">We’re Hiring</a></h3>
        <p><a href="/en-US/about/careers.html">Learn about career opportunities at Mozilla.</a></p>
    </div>

</div>

<!-- Please do not ever remove this comment. -->


        

<div id="footer-divider"><hr /></div>

</div><!-- end #doc -->
</div><!-- end #wrapper -->

    <!-- start #footer -->
    <div id="footer">
    <div id="footer-contents">

        <form id="lang_form" dir="ltr" method="get" action=""><div>
            <label for="flang">Other languages:</label>
            
<select id="flang" name="flang" dir="ltr" onchange="this.form.submit()">    <option value="af">Afrikaans</option>
    <option value="ar">&#1593;&#1585;&#1576;&#1610;</option>
    <option value="as">&#2437;&#2488;&#2478;&#2496;&#2479;&#2492;&#2494;</option>
    <option value="be">&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;</option>
    <option value="bg">&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;</option>
    <option value="bn-BD">&#2476;&#2494;&#2434;&#2482;&#2494; (&#2476;&#2494;&#2434;&#2482;&#2494;&#2470;&#2503;&#2486;)</option>
    <option value="bn-IN">&#2476;&#2494;&#2434;&#2482;&#2494;</option>
    <option value="ca">Catal&#224;</option>
    <option value="cs">&#268;e&#353;tina</option>
    <option value="cy">Cymraeg</option>
    <option value="da">Dansk</option>
    <option value="de">Deutsch</option>
    <option value="el">&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;</option>
    <option value="eo">Esperanto</option>
    <option value="es-AR">Espa&#241;ol (Argentina)</option>
    <option value="es-CL">Espa&#241;ol (Chile)</option>
    <option value="es-ES">Espa&#241;ol (Espa&#241;a)</option>
    <option value="es-MX">Espa&#241;ol (México)</option>
    <option value="et">Eesti keel</option>
    <option value="eu">Euskara</option>
    <option value="en-GB">English (British)</option>
    <option value="en-US" selected="selected">English (US)</option>
    <option value="fa">&#1662;&#1575;&#1585;&#1587;&#1740;</option>
    <option value="fi">Suomi</option>
    <option value="fr">Fran&#231;ais</option>
    <option value="fy-NL">Frysk</option>
    <option value="ga-IE">Gaeilge</option>
    <option value="gl">Galego</option>
    <option value="gu-IN">&#2711;&#2753;&#2716;&#2736;&#2750;&#2724;&#2752;</option>
    <option value="he">&#1506;&#1489;&#1512;&#1497;&#1514;</option>
    <option value="hi-IN">&#2361;&#2367;&#2344;&#2381;&#2342;&#2368; (&#2349;&#2366;&#2352;&#2340;)</option>
    <option value="hr">Hrvatski</option>
    <option value="hu">Magyar</option>
    <option value="id">Bahasa Indonesia</option>
    <option value="is">&#205;slenska</option>
    <option value="it">Italiano</option>
    <option value="ja">&#26085;&#26412;&#35486;</option>
    <option value="ka">&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312; &#4308;&#4316;&#4304;</option>
    <option value="kk">&#1178;&#1072;&#1079;&#1072;&#1179;</option>
    <option value="kn">&#57522;&#38368;&#45736;&#57523;&#36320;&#45736;&#57522;</option>
    <option value="ko">&#54620;&#44397;&#50612;</option>
    <option value="ku">Kurd&#238;</option>
    <option value="lt">Lietuvi&#371;</option>
    <option value="lv">Latvie&#353;u</option>
    <option value="mk">&#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;</option>
    <option value="ml">&#3374;&#3378;&#3375;&#3390;&#3379;&#3330;</option>
    <option value="mr">&#2350;&#2352;&#2366;&#2336;&#2368;</option>
    <option value="nl">Nederlands</option>
    <option value="no">Norsk bokm&#229;l</option>
    <option value="oc">occitan (lengadocian)</option>
    <option value="pa-IN">&#2602;&#2672;&#2588;&#2622;&#2604;&#2624;</option>
    <option value="pl">Polski</option>
    <option value="pt-BR">Portugu&#234;s (do Brasil)</option>
    <option value="pt-PT">Portugu&#234;s (Europeu)</option>
    <option value="rm">Rumantsch</option>
    <option value="ro">Rom&#226;n&#259;</option>
    <option value="ru">&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;</option>
    <option value="sk">Sloven&#269;ina</option>
    <option value="si">&#3523;&#3538;&#3458;&#3524;&#3517;</option>
    <option value="sl">slovensko</option>
    <option value="sq">Shqip</option>
    <option value="sr">&#1089;&#1088;&#1087;&#1089;&#1082;&#1080;</option>
    <option value="sv-SE">Svenska</option>
    <option value="ta">&#2980;&#2990;&#3007;&#2996;&#3021;</option>
    <option value="ta-LK">Tamil (Sri Lanka)</option>
    <option value="te">&#57520;&#42208;&#45446;&#57520;&#45792;&#45441;&#57520;&#38880;&#45441;</option>
    <option value="th">&#3616;&#3634;&#3625;&#3634;&#3652;&#3607;&#3618;</option>
    <option value="tr">T&#252;rk&#231;e</option>
    <option value="uk">&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;</option>
    <option value="vi">Ti&#7871;ng Vi&#7879;t</option>
    <option value="zh-CN">&#20013;&#25991; (&#31616;&#20307;)</option>
    <option value="zh-TW">&#27491;&#39636;&#20013;&#25991; (&#32321;&#39636;)</option>
</select>

            <noscript>
                <div><input type="submit" id="lang_submit" value="Go" /></div>
            </noscript>
        </div></form>

        <ul id="footer-menu">
            <li><a href="/en-US/firefox/">Firefox</a>
                <ul>
                    <li><a href="/en-US/firefox/features/">Features</a></li>
                    <li><a href="/en-US/firefox/performance/">Performance</a></li>
                    <li><a href="/en-US/firefox/security/">Security</a></li>
                    <li><a href="/en-US/firefox/customize/">Customization</a></li>
                    <li><a href="/en-US/firefox/organic/">100% Organic Software</a></li>
                    <li><a href="/en-US/firefox/tips/">Tips and Tricks</a></li>
                    <li><a href="/en-US/firefox/video/">Videos</a></li>
                    <li><a href="/en-US/firefox/3.5.2/releasenotes/">Release Notes</a></li>
                    <li><a href="/en-US/firefox/all.html">Other Systems and Languages</a></li>
                    <li><a href="/en-US/firefox/fastest/">Fastest Firefox</a></li>
                </ul>
            </li>
            <li><a href="https://addons.mozilla.org/" class="external">Add-ons</a>
                <ul>
                    <li><a href="https://addons.mozilla.org/firefox/" class="external">All Add-ons</a></li>
                    <li><a href="https://addons.mozilla.org/firefox/recommended" class="external">Recommended</a></li>
                    <li><a href="https://addons.mozilla.org/firefox/browse/type:1/cat:all?sort=popular" class="external">Popular</a></li>
                    <li><a href="https://addons.mozilla.org/firefox/browse/type:2" class="external">Themes</a></li>
                    <li><a href="https://addons.mozilla.org/firefox/browse/type:4" class="external">Search Engines</a></li>
                    <li><a href="https://addons.mozilla.org/firefox/browse/type:7" class="external">Plugins</a></li>
                </ul>
            </li>
            <li><a href="http://support.mozilla.com/">Support</a>
                <ul>
                    <li><a href="http://support.mozilla.com/en-US/kb/">Firefox Support</a></li>
                    <li><a href="http://www.mozilla.org/support/thunderbird/" class="external">Thunderbird Support</a></li>
                </ul>
            </li>
            <li><a href="/en-US/manyfaces/">Community</a>
                <ul>
                    <li><a href="https://addons.mozilla.org/" class="external">Add-ons</a></li>
                    <li><a href="https://bugzilla.mozilla.org/" class="external">Bugzilla</a></li>
                    <li><a href="http://developer.mozilla.org/" class="external">Mozilla Developer Center</a></li>
                    <li><a href="http://labs.mozilla.com/" class="external">Mozilla Labs</a></li>
                    <li><a href="http://www.mozillamessaging.com/" class="external">Mozilla Messaging</a></li>
                    <li><a href="http://www.mozilla.org/" class="external">Mozilla.org</a></li>
                    <li><a href="http://www.mozillazine.org/" class="external">MozillaZine</a></li>
                    <li><a href="http://planet.mozilla.org/" class="external">Planet Mozilla</a></li>
                    <li><a href="http://quality.mozilla.org/" class="external">QMO</a></li>
                    <li><a href="http://www.spreadfirefox.com/" class="external">Spread Firefox</a></li>
                    <li><a href="http://support.mozilla.com/">Support</a></li>
                </ul>
            </li>
            <li><a href="/en-US/about/">About</a>
                <ul>
                    <li><a href="/en-US/about/whatismozilla.html">What is Mozilla?</a></li>
                    <li><a href="/en-US/about/get-involved.html">Get Involved</a></li>
                    <li><a href="/en-US/press/">Press Center</a></li>
                    <li><a href="/en-US/about/careers.html">Careers</a></li>
                    <li><a href="/en-US/about/partnerships.html">Partnerships</a></li>
                    <li><a href="http://www.mozilla.org/foundation/licensing.html" class="external">Licensing</a></li>
                    <li><a href="http://blog.mozilla.com/" class="external">Blog</a></li>
                    <li><a href="http://store.mozilla.org/" class="external">Store</a></li>
                    <li><a href="http://communitystore.mozilla.org/" class="external">Community Store</a></li>
                    <li><a href="/en-US/about/logo/">Logo Guide</a></li>
                    <li><a href="/en-US/about/contact.html">Contact Us</a></li>
                </ul>
            </li>
        </ul>

        <div id="copyright">
            <p id="footer-links"><a href="/en-US/privacy-policy.html">Privacy Policy</a> &nbsp;|&nbsp; 
            <a href="/en-US/about/legal.html">Legal Notices</a> &nbsp;|&nbsp;
                        <a href="/en-US/legal/fraud-report/index.html">Report Trademark Abuse</a></p>
            <p>Except where otherwise <a href="/en-US/about/legal.html#site">noted</a>, content on this site is licensed under the <br /><a href="http://creativecommons.org/licenses/by-sa/3.0/">Creative Commons Attribution Share-Alike License v3.0</a> or any later version.</p>
        </div>

    </div>
    </div>
    <!-- end #footer -->
    <script type="text/javascript">// <![CDATA[
        var s_code=s.t();if(s_code)document.write(s_code);
    // ]]></script>
    <!-- end SiteCatalyst code version: H.14 -->
    <script type="text/javascript" src="/js/__utm.js"></script>
    <script type="text/javascript" src="/js/track.js"></script>
    

</body>
</html>
gashman@grant-laptop:~$ 

```

---

### Post by nanotube on 2009-08-04
that looks right to me... i have no idea why it's not working - i've been doing test runs here on my machine and everything goes through without a hitch...

---

### Post by Baasha on 2009-08-07
Hi nano,
I had the same problem with my install.  I am running Ubuntuzilla 7.1 with Ubuntu 8.0.4.

I had much the same error messages as posted earlier in this thread.  What was different was that I also had a few messages about failing permissions to backup the cache files.  I wasn't concerned because I have my browser set up to delete the cache every time I shut down.  

Then I read your response in another thread where you told someone to change the permissions from root to user for the whole .mozilla directory, in order to fix another problem.  So even though I didn't care about my cache files I tried it to see if it cleared up some of the error messages.  Then Ubutuzilla installed perfectly.  So you might want to include a line in the instructions about this.

Thanks for a great extension to Ubuntu.

---

### Post by nanotube on 2009-08-07
Hi
Thanks for your comment... I'll make a note of that in the faq :)

---

