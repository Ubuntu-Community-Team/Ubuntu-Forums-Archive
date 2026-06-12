---
title: "Apache2  2.2.22 to .23 and securing a web-server question."
date: 2012-11-01
forum: Server Platforms
---

### Post by Coder68 on 2012-11-01
Ubuntu 12.04 LTS 64bit, Apache2 2.2.22, PHP 5 - All fully updated via Ubuntu repositories.

When will Ubuntu's repository have the Apache2 2.2.23? I can't seem to find anything other then how to install Apache, nothing about release dates. A scan reveals Apache2 2.2.22 has some vulns. 

[http://httpd.apache.org/security/vulnerabilities_22.html](http://httpd.apache.org/security/vulnerabilities_22.html)

     [B]       insecure LD_LIBRARY_PATH handling     
[/B]Apache rates it as low but Rapid7 rates it as severe. 
    [B]       XSS in mod_negotiation when untrusted uploads are supported     
[/B]Apache rates as low, Rapid7 rates as moderate

Neither of these have public exploits available at this time, so I am not super worried, but I would like to be as secure as possible. 
------
I am building this Web-server for our DMZ and want to make sure it is as secure as possible. I have installed Apache2 and PHP5 and installed and configured: 

[LIST=1]
[*]modsecuirty
[*]Only opened port 80 in the FW
[*]Installed and configured php5-suhosin
[*]Removed test.php, info.php, i.php, phpinfo.php, etc...
[*]This server will be behind an enterprise level firewall/IPS/IDS.
[/LIST]

I think I am down to disabling unwanted services, disabling accounts, disable Apache banner/HTTP trace request, disable directory indexing, disable WebDav, chroot Apache, turn off any webstats, enable PHP basedir. These are things that I have found on Google. Some may not apply... but I know services does!

What services should I disable? I find lots of how to turn off Apache2... but not the what services except Apache/PHP! 

Anything else I should do to maximize security?

Thank you,

C68

---

