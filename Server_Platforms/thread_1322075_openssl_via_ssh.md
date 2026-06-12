---
title: "openssl via ssh?"
date: 2009-11-10
forum: Server Platforms
---

### Post by maclenin on 2009-11-10
I've assembled a .php script that encrypts data using openssl.

The script has been tested - successfully - in a local server environment (127.0.0.1).

However, upon moving the script to a new host, I've lost access to openssl...

```
Error: /usr/bin/openssl not found
```

...essentially, I am trying to figure out how to re-engage openssl within the new server environment...

1. Do I simply need to revise/confirm the path to openssl within the new environment?
2. Could it be an issue of "rights" - that the domain (user) from which I am running the script needs "rights" to access openssl at the root (/usr/bin) level of the new server environment?
3. Do I need ssh to access /usr/bin within the new environment?
4. Thoughts?

...thanks for any suggestions....

---

### Post by McCoy on 2009-11-10
First thing to check, is if the new host even has openssl... You have shell access to it? If so, just write "which openssl" in the console and it should tell you where it is. If it's not found, then you'll have to install it. Is it a dedicated or shared server?

---

### Post by maclenin on 2009-11-10
The new host is one of these: [http://mediatemple.net/webhosting/dv/](http://mediatemple.net/webhosting/dv/) ... a virtual dedicated server. I am quite certain it has openssl....

I do not have shell access to the server. I assume the only way for me to access the shell - to run "which" commands, for example - would be to connect via ssh - or through physical access to the server?

With regard to the .php script itself - might there be other ways to facilitate a script's access to executables in the server's root directory? Perhaps through modifying domain/user privileges?

Thanks for the reply.

---

### Post by McCoy on 2009-11-10
If it's a VPS then I'm 99.9% sure you have shell access. Indeed, you have to connect through SSH to gain access. Check in the help / login documentation of your account if they are using a custom port for SSH instead of the standard port 22, providers sometines do this to prevent hacking attempts and it can make you incorrectly think that you don't have shell access because you can't connect.

If they provide SSH access then it's quite sure openssh will be installed so it will be most likely a path issue, and by changing it to whatever "which" returns should make your script work. And even if it's not installed you can just install it yourself easily with yum (it's like apt-get but that's what they use in CentOS).

If not, then there can be permission issues that will have to be looked more throughtly, but try this first.

---

### Post by maclenin on 2009-11-10
Thanks, McCoy....

So, just to clarify...

...I have ftp access to one of the domains on the VPS.
...It's from a .php script within this domain that I am attempting to access openssl.
...I am not the server admin - my access is (thus far) limited only to management of the directories within my domain.
...The question, I think - is how would a script running from within my domain be able to access openssl?

Would I need to access the server via ssh - or could the permissions be modified at the level of my domain to grant "executable" access to the root dirs?

In fact, my preference would be to be able to run the script without having to use ssh....

---

### Post by McCoy on 2009-11-10
I see.

Another way is to make a small php script, like this:

```

<?php
echo exec('which openssl');
?>

```

Upload it and run it from your browser, and it should tell you the correct path.

I really think is a path issue and not a permissions issue, or you won't get a "not found" error but a permissions error.

---

### Post by maclenin on 2009-11-10
Ran this...
```

echo "text<br />";
echo exec ('which openssl');
echo "<br />";
echo "text";

```
...received this...
```

text

text

```
...thoughts?

I am beginning to think that openssl might not be installed on this server....

---

### Post by McCoy on 2009-11-10
I tried it in my CentOS dedicated server and it worked. It returned

```

text
/usr/bin/openssl
text

```

"which" should return something like

```

/usr/bin/which: no openssl in (//bin:/usr/local/bin:/bin:/usr/bin)

```

in case the file was not found. To check for this, you will most likely need to redirect the stderr output to stdout so you can see this. Use this:

```

echo exec('which openssl 2>&1');

```

Just to be sure.

---

### Post by maclenin on 2009-11-11
My updated script...
```

echo "text<br />";
echo exec ('which openssl');
echo "<br />";
echo exec ('which openssl 2>&1');
echo "<br />";
echo "text";

```
...with very similar output...
```

text


text

```
...as per a chat with the server admin I am now quite certain openssl is not installed on the server in question...however, the "2>&1" variant should have told me so, yes?

Thanks for your help with this process!

---

### Post by McCoy on 2009-11-11
That's strange, that "which" gave no output at all, not even in stderr... maybe you don't have execute privileges. Try to put "error_reporting (E_ALL);" at the beggining of the script to see if you get any error.

Anyway, if the server admin told you that openssl is not installed, then installing it is a mandatory step to take. He should be able to do it through SSH with yum in just one command.

---

### Post by maclenin on 2009-11-11
```
error_reporting (E_ALL);
```
...yielded no changes! Perhaps I do not have execute privileges....

Are there diff. levels of privilege where .php is concerned - i.e. I can only run "simple" scripts - but if I attempt to run "executables" - I would not be able to - I need to be assigned the specific privilege to execute?

Thanks, again, for walking me through this....

Edit: Perhaps it's not a .php issue re: execute - but a domain/user privileges issue?

---

### Post by McCoy on 2009-11-11
Usually php scripts have the same permissions as the user that the server process uses. This user is usually named "psaserv" -typical for plesk- or "www-data" -this is the case of ubuntu server- or "apache" or stuff like that.

More fine-grain permissions can ve given via .htaccess files and the like, but usually it's just equal to the server user. So if for some reason you can't execute files, second thing to check is if you can do it by loging in with the server username and trying to execute that command. It's very possible you won't be able because of lack of permissions, just like from the PHP script. You will have to do this through SSH though, so not an option for you.

There is also the possibility that your account is chrooted, this effectively denies you access to the real server root as you will only see a fake one. Or even being restricted by a defined open_basedir in PHP directly.

But anyway like said before, first stip is to get openssh installed :) 

Good luck!

---

### Post by maclenin on 2009-11-13
Thanks **McCoy** for your perseverance! I learned a bunch these past few days! I plan to take your knowledge with me when I start managing my own server "farm".... For now, I continue to test my .php scripts via 127.0.0.1 - with amplomb!

Thanks, again!

---

