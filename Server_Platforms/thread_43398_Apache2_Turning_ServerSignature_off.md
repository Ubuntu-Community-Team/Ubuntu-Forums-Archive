---
title: "Apache2: Turning ServerSignature off"
date: 2005-06-21
forum: Server Platforms
---

### Post by loon on 2005-06-21
How in the world, can I make Apache2 stop displaying 
"Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4 Server at xx.xx.xx.xx Port 80"

bleh  [-X

FIX:
sudo vi /etc/apache2/apache2.conf

add line at the bottom:
ServerTokens Prod

save and close (shift+colon wq enter [if in vi])

sudo /etc/init.d/apache2 restart

Now displayed:
"Apache Server at xx.xx.xx.xx Port 80"


Thanks for all your help people. And good discussion by the way.  :)

---

### Post by LordHunter317 on 2005-06-21
You can turn off the ServerSignature, but that only effects error pages AFAIK.

Why do you care?  It's not like any of the information it displays matters.  An attacker won't bother to look at it.

To be clear, the directive is ServerSignature, and it's in /etc/apache2/sites-enabled/000-default in a stock installation.

---

### Post by GrumpySimon on 2005-06-22
Apparently a number of worms check the server signature to know which versions to attack, so maybe it does matter. I'm not sure of any worms attacking current versions of Apache, but better safe than sorry.

Anyway, open up your httpd.conf file, and change the ServerTokens line. Yours will say something like 
```

ServerTokens Full

```

Change it to something like 
```

SeverTokens Prod

```

Which will just show 'Apache'. 

The full list of settings for the ServerTokens parameter is [here](http://httpd.apache.org/docs-2.0/mod/core.html#servertokens).

As far as I'm aware ServerTokens was supposed to replace/override ServerSignature since 2.0.44.

--Simon

---

### Post by jdong on 2005-06-22
[QUOTE=LordHunter317]Why do you care?  It's not like any of the information it displays matters.  An attacker won't bother to look at it.[/QUOTE]

Actually, during the pre-attack phase, Apache version is a great way of finding an easily available attack.

In addition, by putting two and two together (Ubuntu + Apache version), one can figure out what version of Ubuntu someone's running. This information can be deadly if the server offers a lot of daemons from Universe, as they aren't security-reviewed or kept up-to-date for the 6-month release.

---

### Post by LordHunter317 on 2005-06-22
> **GrumpySimon]Apparently a number of worms check the server signature to know which versions to attack, so maybe it does matter.[/quote]I've **yet** to see any worm that does this, for any piece of Internet connected software.

Remember all the infamous IIS worms (e.g., Code Red)  that attacked the world?  They didn't even check to see if the machine was IIS.  They just tried to run their exploit.  If it worked, great, one more zombie.  If not, who cares said:**
> Actually, during the pre-attack phase, Apache version is a great way of finding an easily available attack.The point is, **nobody bothers** because they can just run a much larger-scale and automated dumb attack and exploit more boxes than they would if they tried one by one and checked versions.

Automated attackers don't care about failed attempts; they have no reason to.

And if you're attacked by an actual human; they'll try all the exploits they can anyway if they're really determined to get in.  A good attacker is smart enough to know that version string can't be trusted (it could be spoofed).  So they'll try a whole range of exploits anyway to be certain.

> This information can be deadly if the server offers a lot of daemons from Universe, as they aren't security-reviewed or kept up-to-date for the 6-month release.But it's not.  Why would I attempt to badly infer information when I can just portscan the box and figure out all the daemons you're running and attempt to exploit them anyway?  It doesn't make sense: I'm wasting my time for information of somewhat dubious value.

---

### Post by GrumpySimon on 2005-06-23
[QUOTE=LordHunter317]I've **yet** to see any worm that does this, for any piece of Internet connected software.[/quote]

[Linux.Slapper.Worm](http://www.informit.com/articles/article.asp?p=366891&seqNum=3&rl=1):

> 
Listing 9.3 The Bogus GET Request of Linux/Slapper

GET / HTTP/1.1\r\n\r\n

The worm expects that Apache Web servers return an error message to this request; Apache returns the message shown in Listing 9.4 to the attacker node:
Listing 9.4 Apache Web Server's Answer

```

HTTP/1.1 400 Bad Request
Date: Mon, 23 Feb 2004 23:43:42 GMT
Server: Apache/1.3.19 (UNIX) (Red-Hat/Linux) mod_ssl/2.8.1 
OpenSSL/0.9.6 DAV/1.0.2 PHP/4.0.4pl1 mod_perl/1.24_01
Connection: close
Transfer-Encoding: chunked
Content-Type: text/html; charset=iso-8859-1

```
Note the Server: Apache keywords in the error message. The returned data also has information about the actual version number of the Web server, which is 1.3.19 in this example.

The worm checks whether the error message is coming from an Apache server by matching the server information. Then it uses a table filled with architecture and version information numbers (shown in Listing 9.5) to see if the target is compatible with the attack.


Also, if memory serves, the recent PHP Santy worm, as well as a number of phpBB2 exploits have checked version numbers for vulnerable versions, or used google to track down vulnerable versions. Sure - it's not Apache related, but the script kiddies are doing it.

--Simon

---

### Post by LordHunter317 on 2005-06-23
Ahh, but the analysis isn't quite correct.  The code in question does this:```
if (strncmp(a,"Apache",6)) exit(0);
        for (i=0;i<MAX_ARCH;i++) {
                if (strstr(a,architectures[i].apache) && strstr(a,architectures[
i].os)) {
                        arch=i;
                        break;
                }
        }
        if (arch == -1) arch=9;
```

So if it doesn't find an known combination, it selects a default one.  The reason it does this is because OpenSSL isn't ABI compatible across releases or even distributions, so the address of the exploitable code isn't a constant.  A more "intelligent" exploit might try multiple attempts and guessing, but such things are rarely perfect and difficult to pull off remotely.

So yes, it does do version indentification.  But not publishing the version information wouldn't stop the attack; the worm would still try.  It might not even stop the exploit.  It would depend on what version of the software you're running. 

So, in order to gain security, you still must patch and be up to date. 

The ABI issue with OpenSSL is a weird case.  Lots of other exploitable software and cases wouldn't have this problem.

---

### Post by janerds on 2005-07-10
I think SeverTokens Prod is not enough !
You can open ap_release.h to change Apache server signal such as Microsoft IIS
Or you can use mod_headers to change it,
Or you can use mod_security (modsecurity.org)
--j

---

### Post by bradsorensen on 2005-11-22
First let me say I need to resolve an vulnerability callled : Apache web server token has not been set - High SANS Top 20.

The fix says to add lines Server Tokens Prod and ServerSignature Off

Im not sure how to edit this http.conf file or even if this is the right file?

Ive listed below what I did please can someone please correct my mistakes and provide instructions to a newbie in terminal including commands to make the necessary changes.

I opened a terminal window typed sudo vi /etc/httpd/http.conf 
Enterd password and it opens the file httpd.conf 
I scrolled down to a section that says 
ServerSignature On
I changed it to Off
Shift : wq enter to save and exit
Is this enough? 
I did not see a scetion called ServerTokens in this file?

Please advise...
Thanks in advance

:confused:

---

### Post by loon on 2005-11-28
[QUOTE=bradsorensen]First let me say I need to resolve an vulnerability callled : Apache web server token has not been set - High SANS Top 20.

The fix says to add lines Server Tokens Prod and ServerSignature Off

Im not sure how to edit this http.conf file or even if this is the right file?

Ive listed below what I did please can someone please correct my mistakes and provide instructions to a newbie in terminal including commands to make the necessary changes.

I opened a terminal window typed sudo vi /etc/httpd/http.conf 
Enterd password and it opens the file httpd.conf 
I scrolled down to a section that says 
ServerSignature On
I changed it to Off
Shift : wq enter to save and exit
Is this enough? 
I did not see a scetion called ServerTokens in this file?

Please advise...
Thanks in advance

:confused:[/QUOTE]


Do what I do on my first post but instead add the ServerTokens Off.
That is if you are running Apache2.
Apache1.x has it in the httpd.conf, just search for it. It maybe commented out. Removed the # in front of the line.
-

Apache2:

sudo vi /etc/apache2/apache2.conf
Hit "I" for Insert and add ServerTokens Off at the bottom.
Shift :
wq [Enter]
sudo /etc/init.d/apache2 restart

Apache1.3:

sudo vi /etc/apache/httpd.conf
Find the #ServerTokens Full (line 548 in my config)
and hit the "d" (for delete) in front of the # to remove it.
Shift :
wq [Enter]
sudo /etc/init.d/apache restart

Also note that ServerSignature on is right above it. Turn that to off.

Hope this helps and sorry its been almost a week :)

---

### Post by Danielle on 2005-11-28
if you want to check your server you can go into synaptic and get nikto to check for server vulnerabilies.

---

### Post by loon on 2005-11-28
[QUOTE=Danielle]if you want to check your server you can go into synaptic and get nikto to check for server vulnerabilies.[/QUOTE]


Is that a CLI program?? I have no X on my server.

---

### Post by Danielle on 2005-11-28
[QUOTE=loon]Is that a CLI program?? I have no X on my server.[/QUOTE]
sorry, i've never used it. i've got a l337 friend who uses it lol. do a search for it. i know it's very good though

---

### Post by Danielle on 2005-11-28
oh, sorry lol i thought you were talking about a programing language or something. it's very easy to use. and yes it is.

---

