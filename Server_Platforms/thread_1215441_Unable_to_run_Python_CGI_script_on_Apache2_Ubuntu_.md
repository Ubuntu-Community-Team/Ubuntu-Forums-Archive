---
title: "Unable to run Python CGI script on Apache2 Ubuntu 9.04 Server"
date: 2009-07-17
forum: Server Platforms
---

### Post by hetx on 2009-07-17
As far as I understand it's supposed to run straight outta the box but I just get Internal Server Errors.

This is the site conf file
```
    ScriptAlias /cgi-bin/ /home/user/cgi-bin/
    <Directory /home/user/cgi-bin/>
        AddHandler cgi-script cgi py
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
```And this is the error log
```
[Fri Jul 17 11:52:53 2009] [error] [client IP] /usr/bin/env: , referer: http://user.homelinux.com/cgi101.html
[Fri Jul 17 11:52:53 2009] [error] [client IP] python\r, referer: http://user.homelinux.com/cgi101.html
[Fri Jul 17 11:52:53 2009] [error] [client IP] : No such file or directory, referer: http://hetx.homelinux.com/cgi101.html
[Fri Jul 17 11:52:53 2009] [error] [client IP] , referer: http://user.homelinux.com/cgi101.html
```And this is the Python script
```
#!/usr/bin/env python 
import cgi 
form = cgi.FieldStorage()                # parse form data 
print "Content-type: text/html\n"        # hdr plus blank line 
print "<title>Reply Page</title>"        # html reply page 
if not form.has_key('user'): 
    print "<h1>Who are you?</h1>" 
else: 
    print "<h1>Hello <i>%s</i>!</h1>" % cgi.escape(form['user'].value) 
```I'm completely stumped. Grateful for any help! Also, I know this may be an Apache specific problem, but it could just as well be permissions or the like (the cgi script has executable permission) and associated with the server. Like I said, I don't know what's wrong.

---

### Post by hetx on 2009-07-19
Still desperately looking for an answer or even a pointer to where I could go for help.

---

### Post by windependence on 2009-07-19
Does this file exist on the server?

[http://hetx.homelinux.com/cgi101.html](http://hetx.homelinux.com/cgi101.html)

-Tim

---

### Post by hetx on 2009-07-19
It's on port 8090, could that be what's messing it up? I'm just using the server to try stuff out so I figured I'd keep it off 80

[http://hetx.homelinux.com:8090/cgi101.html](http://hetx.homelinux.com:8090/cgi101.html)

---

### Post by windependence on 2009-07-19
It doesn't matter inside your network. No one can get to it unless 80 is forwarded to your server at the router level. You can leave it at 80 and use it inside the network just fine.

-Tim

---

### Post by hetx on 2009-07-19
You're right ofcourse, but the problem is still there. I don't have alot of experience with apache error logs, I'm not sure how to interpret it. Is it not finding the interpreter?

---

### Post by windependence on 2009-07-19
Yeah, you probably need to load some Python libraries.

Can you post your Apache error log? It should be in /var/log.

-Tim

---

### Post by hetx on 2009-07-19
I did, it's up in the first post under "error log".

Here's some more possibly pertinent information. A simple Perl script worked just fine [http://hetx.homelinux.com:8090/cgi-bin/perl.pl](http://hetx.homelinux.com:8090/cgi-bin/perl.pl)

And this is the footer of the Internal Server Error message. Am I supposed to have three python-interpreters? -_-

Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2 Server at hetx.homelinux.com Port 8090

---

### Post by windependence on 2009-07-19
Where is this file located ON YOUR SERVER MACHINE?  
[http://user.homelinux.com/cgi101.html](http://user.homelinux.com/cgi101.html)

This is your big clue here:

```
No such file or directory, referer: [http://hetx.homelinux.com/cgi101.html](http://hetx.homelinux.com/cgi101.html)
```

Either the file isn't there, OR it's not in your user's path. It has nothing to do with Python or Apache, it can't even load the file because it can't find it.


-Tim

---

### Post by hetx on 2009-07-19
The error log was edited (sudden attack of paranoia). The file is in apache document root. [http://hetx.homelinux.com:8090/cgi101.html](http://hetx.homelinux.com:8090/cgi101.html)

I'm sorry if that confused you.

---

### Post by windependence on 2009-07-20
OK.....but exactly what is the path to your doc root?

-Tim

---

### Post by hetx on 2009-07-20
DocRoot is /home/hetx/default/ (in which there is a cgi101.html)

And ScriptAlias is /home/hetx/cgi-bin/ (in which there is a cgi101.py)

Now when I access cgi101.py from within the network it tries to download the script instead of running it. I put another script in Script Alias "peoplecgi.py" it acts the same way.

```
[Mon Jul 20 10:47:46 2009] [error] [client 90.229.229.160] (8)Exec format error: exec of '/home/hetx/cgi-bin/peoplecgi.py' failed, referer: http://erik.koangen.se/cgi-bin/peoplecgi.py
[Mon Jul 20 10:47:46 2009] [error] [client 90.229.229.160] Premature end of script headers: peoplecgi.py, referer: http://erik.koangen.se/cgi-bin/peoplecgi.py
```

and also gives Internal Server Error on the hetx.homelinux.com:8090 address

Both are executable.

```
-rwxrwxrwx 1 root root  362 2009-07-18 17:08 cgi101.py
-rwxrwxrwx 1 hetx hetx  359 2009-07-16 18:06 cgi101.py~
-rwxrwxrwx 1 hetx hetx 3027 2009-07-16 18:06 peoplecgi.py
-rwxr-xr-x 1 root root   77 2009-07-20 00:27 perl.pl

```

The perl script works just fine
[http://hetx.homelinux.com:8090/cgi-bin/perl.pl](http://hetx.homelinux.com:8090/cgi-bin/perl.pl)

---

### Post by windependence on 2009-07-20
I am almost positive this has to do with the authority of the Apache user vs. your authority when you run the script from an interactive session. Here is some info from the Apache docs for your error:
> 
What does it mean         when my CGIs fail with "Premature end of script         headers"?           It means just what it says: the server was expecting a         complete set of HTTP headers (one or more followed by a         blank line), and didn't get them.
          The most common cause of this problem is the script         dying before sending the complete set of headers, or         possibly any at all, to the server. To see if this is the         case, try running the script standalone from an interactive         session, rather than as a script under the server. If you         get error messages, this is almost certainly the cause of         the "premature end of script headers" message. [COLOR=Red]**Even if the         CGI runs fine from the command line, remember that the         environment and permissions may be different when running         under the web server. The CGI can only access resources         allowed for the [User]("http://httpd.apache.org/docs/1.3/mod/core.html#user") and [Group]("http://httpd.apache.org/docs/1.3/mod/core.html#group")         specified in your Apache configuration. In addition, the         environment will not be the same as the one provided on the         command line, but it can be adjusted using the directives         provided by [mod_env]("http://httpd.apache.org/docs/1.3/mod/mod_env.html").**[/COLOR]
          The second most common cause of this (aside from people         not outputting the required headers at all) is a result of         an interaction with Perl's output buffering. To make Perl         flush its buffers after each output statement, insert the         following statements around the print or         write statements that send your HTTP         headers:
          {
            local ($oldbar) = $|;
            $cfh = select (STDOUT);
            $| = 1;
            #
            # print your HTTP headers here
            #
            $| = $oldbar;
            select ($cfh);
           }          This is generally only necessary when you are calling         external programs from your script that send output to         stdout, or if there will be a long delay between the time         the headers are sent and the actual content starts being         emitted. To maximize performance, you should turn         buffer-flushing back off (with $| = 0         or the equivalent) after the statements that send the         headers, as displayed above.
          If your script isn't written in Perl, do the equivalent         thing for whatever language you are using         (e.g., for C, call fflush() after         writing the headers).
          Another cause for the "premature end of script headers"         message are the RLimitCPU and RLimitMEM directives. You may         get the message if the CGI script was killed due to a         resource limit.
          In addition, a configuration problem in [suEXEC]("http://httpd.apache.org/docs/1.3/suexec.html"), mod_perl, or another         third party module can often interfere with the execution         of your CGI and cause the "premature end of script headers"         message.[http://httpd.apache.org/docs/1.3/misc/FAQ-F.html#premature-script-headers](http://httpd.apache.org/docs/1.3/misc/FAQ-F.html#premature-script-headers)

Emphasis is mine. The user the script runs under and the environment are always going to be different than when you run them from an interactive session. It may be difficult for us to pin down, but it CAN be fixed.

Did you happen to write this for Windoze and then move it to Linux or switch platforms for any reason? The other error you got indicates this could be the problem or again the environment it's run in.

-Tim

---

### Post by hetx on 2009-08-01
I wouldn't know where to start. What needs to run with other permissions? User added to what group? This is getting over my head, considering giving reinstallation a chance.

The script is supposed to work in the Linux environment. It runs fine from command line. It is very simple.

```
#!/usr/bin/python 2.6
import cgi 
form = cgi.FieldStorage()                # parse form data 
print "Content-type: text/html\n"        # hdr plus blank line 
print "<title>Reply Page</title>"        # html reply page 
if not form.has_key('user'): 
    print "<h1>Who are you?</h1>" 
else: 
    print "<h1>Hello <i>%s</i>!</h1>" % cgi.escape(form['user'].value) 
```

I've even tried it with different interpreter paths. The only thing I can think of that may have messed things up is that I added a pythonmod to the Apacheserver, I don't really remember why I did that.

---

