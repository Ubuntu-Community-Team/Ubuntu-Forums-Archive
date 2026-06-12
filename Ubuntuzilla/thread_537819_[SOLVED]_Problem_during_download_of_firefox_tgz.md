---
title: "[SOLVED] Problem during download of firefox tgz"
date: 2007-08-29
forum: Ubuntuzilla
---

### Post by okparanoid on 2007-08-29
> wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/)[DIRECTORY]  fr . . . . . . . . . . . . . . . . . . .    [Jul 30 03:55]/firefox-2.0.0.6.tar.gz

wget doesn't work during the installation script, however the url seems to be missformated...

Is This a bug of the ubuntuzilla 4.4.0 ?
Thanks for reply

PS : I use a proxy (with http/ftp_proxy variable environment) and have no problem with wget to use in this configuration.

---

### Post by ajgreeny on 2007-08-29
Why download the tgz?  Version 2.0.0.6 is in the repos for feisty.
sudo apt-get firefox
will do it all for you without any fiddling or playing with tar.

---

### Post by okparanoid on 2007-08-29
Like forum suggest it, i talk about the ubuntuzilla script...

The error appends when he's trying to install firefox

I think that's interesting to let ubuntuzilla "do it all for me" in place of repos, specially for thunderbird, because the version will be mostly "up to date".

---

### Post by nanotube on 2007-08-29
> **okparanoid said:**
> wget doesn't work during the installation script, however the url seems to be missformated...

Is This a bug of the ubuntuzilla 4.4.0 ?
Thanks for reply

PS : I use a proxy (with http/ftp_proxy variable environment) and have no problem with wget to use in this configuration.

hi

generally speaking, i doubt this is a bug in ubuntuzilla, because i have tested it before i released it - and i just tested it again right now before replying, and the download went fine. so i suspect it is something relating to your configuration, or possibly a transient network error in reaching the mozilla server.

could you please post the complete output of the script, from the beginning all the way up to when it errors out?
that'll help me figure out what's going on with you. :)

---

### Post by okparanoid on 2007-08-30
I will do it at work on monday, perhaps the proxy server used to access the web make some troubles...

However if i understand well how the python script works he's trying to list all of directories in ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/"lastversion"/linux-i686/
and ask the user to choose one of it.

When it's executed at works it's give me a non well justified list of lines in this style : choice number and "[DIRECTORY] fr . . . . . . . . . . . . . . . . . . . [Jul 30 03:55]" in place of just choice number and "fr" i presume.

So instead of directories name like "fr" or "eu" or "fi" the request list have some nasty waste with it. 

Thanks

---

### Post by nanotube on 2007-08-30
> **okparanoid said:**
> I will do it at work on monday, perhaps the proxy server used to access the web make some troubles...

However if i understand well how the python script works he's trying to list all of directories in ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/"lastversion"/linux-i686/
and ask the user to choose one of it.

When it's executed at works it's give me a non well justified list of lines in this style : choice number and "[DIRECTORY] fr . . . . . . . . . . . . . . . . . . . [Jul 30 03:55]" in place of just choice number and "fr" i presume.

So instead of directories name like "fr" or "eu" or "fi" the request list have some nasty waste with it. 

Thanks

hmm... ok, well, post the output, and we'll see how it goes.
if the problem persists, also post the output when running with the '-d' parameter - that will make even more detailed debug output for troubleshooting purposes.

---

### Post by okparanoid on 2007-09-03
> root@xxxx:/home/loic# ubuntuzilla.py -a install -p firefox -d
Your commandline options:
{'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'mirror': 'releases.mozilla.org', 'action': 'install', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu'], 'targetdir': '/opt'}
Debug mode ON.

Welcome to the Ubuntuzilla Firefox script version 4.4.0

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Apt package name: firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 2.0.0.6. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': y
['Current directory is /pub/mozilla.org/firefox/releases/2.0.0.6/linux-i686/\n', '\n', '[DIRECTORY]  Parent Directory\n', '[DIRECTORY]  af . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ar . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  be . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  bg . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ca . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  cs . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  da . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  de . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  el . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  en-GB. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  en-US. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  es-AR. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  es-ES. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  eu . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  fi . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  fr . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  fy-NL. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ga-IE. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  gu-IN. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  he . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  hu . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  it . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ja . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ka . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ko . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ku . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  lt . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  mk . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  mn . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  nb-NO. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  nl . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  nn-NO. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  pa-IN. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  pl . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  pt-BR. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  pt-PT. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ro . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  ru . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  sk . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  sl . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]\n', '[DIRECTORY]  sv-SE. . . . . . . . . . . . . . . . . .    [Jul 30 05:56]\n', '[DIRECTORY]  tr . . . . . . . . . . . . . . . . . . .    [Jul 30 05:56]\n', '[DIRECTORY]  xpi. . . . . . . . . . . . . . . . . . .    [Jul 27 22:10]\n', '[DIRECTORY]  zh-CN. . . . . . . . . . . . . . . . . .    [Jul 30 05:56]\n', '[DIRECTORY]  zh-TW. . . . . . . . . . . . . . . . . .    [Jul 30 05:56]\n']
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. [DIRECTORY]  af . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   1. [DIRECTORY]  ar . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   2. [DIRECTORY]  be . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   3. [DIRECTORY]  bg . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
  4. [DIRECTORY]  ca . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   5. [DIRECTORY]  cs . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   6. [DIRECTORY]  da . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   7. [DIRECTORY]  de . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
  8. [DIRECTORY]  el . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]   9. [DIRECTORY]  en-GB. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  10. [DIRECTORY]  en-US. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  11. [DIRECTORY]  es-AR. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 12. [DIRECTORY]  es-ES. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  13. [DIRECTORY]  eu . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  14. [DIRECTORY]  fi . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  15. [DIRECTORY]  fr . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 16. [DIRECTORY]  fy-NL. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  17. [DIRECTORY]  ga-IE. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  18. [DIRECTORY]  gu-IN. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  19. [DIRECTORY]  he . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 20. [DIRECTORY]  hu . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  21. [DIRECTORY]  it . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  22. [DIRECTORY]  ja . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  23. [DIRECTORY]  ka . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 24. [DIRECTORY]  ko . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  25. [DIRECTORY]  ku . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  26. [DIRECTORY]  lt . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  27. [DIRECTORY]  mk . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 28. [DIRECTORY]  mn . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  29. [DIRECTORY]  nb-NO. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  30. [DIRECTORY]  nl . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  31. [DIRECTORY]  nn-NO. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 32. [DIRECTORY]  pa-IN. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  33. [DIRECTORY]  pl . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  34. [DIRECTORY]  pt-BR. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  35. [DIRECTORY]  pt-PT. . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 36. [DIRECTORY]  ro . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  37. [DIRECTORY]  ru . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  38. [DIRECTORY]  sk . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]  39. [DIRECTORY]  sl . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]
 40. [DIRECTORY]  sv-SE. . . . . . . . . . . . . . . . . .    [Jul 30 05:56]  41. [DIRECTORY]  tr . . . . . . . . . . . . . . . . . . .    [Jul 30 05:56]  42. [DIRECTORY]  zh-CN. . . . . . . . . . . . . . . . . .    [Jul 30 05:56]  43. [DIRECTORY]  zh-TW. . . . . . . . . . . . . . . . . .    [Jul 30 05:56]

Enter your choice of localization (integer, from 0 to 43): 15
You have chosen localization [DIRECTORY]  fr . . . . . . . . . . . . . . . . . . .    [Jul 30 05:55]. Is that correct [y/n]?
Please enter 'y' or 'n':                                                        

Thanks

---

### Post by nanotube on 2007-09-03
hi
well... it looks like for some reason your w3m output is different from mine.

i have changed the code to make the line parsing more robust (i hope). please try this update, and report if it works as expected for you.

(file attached).

---

### Post by okparanoid on 2007-09-04
sorry i'm using the amd64 bits version...

Thanks a lot

---

### Post by nanotube on 2007-09-04
> **okparanoid said:**
> sorry i'm using the amd64 bits version...

Thanks a lot

ok, attached that one as well to the previous post. :)

---

### Post by okparanoid on 2007-09-07
work's fine !

thanks !

---

### Post by okparanoid on 2007-09-07
Would be great if the script check if the gpg key is already in the gpg db before downloading it.

For example my proxy forbids the gpg key download so i have manually add it to the gpg trusted keys but the script try to download it again and fails ( i have temporally edited the python script to skip the download)...

In an other way i have this message at the end of thunderbird's installation :
> The new Thunderbird version 2.0.0.6 has been installed successfully. Thank you for using Ubuntuzilla.

Would you like to set up automatic update checking for the official Mozilla build of Thunderbird (recommended)? This feature will regularly check for updates to _**Firefox**_, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n]

It's not a "bug" but Firefox string is used in place of Thunderbird ;).

:KS

---

### Post by nanotube on 2007-09-08
> **okparanoid said:**
> Would be great if the script check if the gpg key it's already in the gpg db before downloading it.

For example my proxy forbids the gpg key download so i have manually add it to the gpg trusted keys but the script try to download hit again and fails ( i have temporally edited the python script to skip the download)...

In an other way i have this message at the end of thunderbird's installation :


It's not a "bug" but Firefox string is used in place of Thunderbird ;).

:KS

thanks for your suggestions and the typo (paste-o) pointout. i'll put those into the next version of ubuntuzilla. :)

---

