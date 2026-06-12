---
title: "Problem with Plesk 12.5 and extensions on Ubuntu server"
date: 2015-11-01
forum: Server Platforms
---

### Post by Laurent_Rathle on 2015-11-01
Hello,

I have a server with [COLOR=#000000][FONT=Open Sans]Ubuntu 14.04.3 LTS&#8236; and Plesk [/FONT][/COLOR][COLOR=#000000][FONT=Open Sans]12.5.30. Each time I try to install a Plesk extension, either from the web admin interface or with the line command after [/FONT][/COLOR][FONT=Open Sans, Helvetica Neue, Helvetica, sans-serif][COLOR=#000000]downloading the extension on my server, I get an error like this :

[/COLOR][/FONT]plesk bin extension --install google-authenticator.zipPHP Warning: ZipArchive::extractTo(/opt/psa/tmp/modules0MlLB/.): failed to open stream: Is a directory; File: /opt/psa/admin/plib/Package.php, Line: 57
 Corrupted meta.xml file.
 exit status 1

When I unzip the extension file, I get this structure :
ls
htdocs  _meta  meta.xml  plib

It's the same structure for all extensions. I've asked without success on the Plesk forums. I'm asking here because I've installed some extensions on a Debian based server and I didn't get this error. It only occurs with Ubuntu. Someone told me it could be because of Apparmor, but I've removed it already because of problems with bind. I've looked in /var/log, but I haven't found any file which would give me more clues on what is generating such an error.

Thank you

---

### Post by Laurent_Rathle on 2015-11-01
I found a way to install my extensions with a Plesk line command which works :

[http://download1.parallels.com/Plesk/Doc/en-US/online/plesk-unix-cli/index.htm?fileName=71031.htm](http://download1.parallels.com/Plesk/Doc/en-US/online/plesk-unix-cli/index.htm?fileName=71031.htm)

This way I download them on my server and I can install them without problems :)

---

