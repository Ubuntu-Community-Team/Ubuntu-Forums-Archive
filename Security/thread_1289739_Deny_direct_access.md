---
title: "Deny direct access?"
date: 2009-10-12
forum: Security
---

### Post by weirdbeardmt on 2009-10-12
Hi

I have a Ubuntu box running motion setup and working well. It serves two webcams. It uses mjprox to serve the streams out over port 80.

I have used .htaccess to password protect the folder, but there's nothing stopping someone going directly to the script in cgi-bin.

Is there anyway to stop someone going direct to cgi-bin? i.e., somehow only limit access to the stream via the specified folder?

---

### Post by Agent ME on 2009-10-12
What script do you have in cgi-bin? I haven't any experience with CGI scripts actually.

Surely you could just put an .htaccess file in that folder, with this text:
```
order deny, allow
deny from all
```

---

### Post by weirdbeardmt on 2009-10-13
The script is a small program that takes the video stream from the Motion server running on the machine and makes it available on port 80. 

Thinking about it more sensibly, I can't deny all access to that folder as I have other scripts in there that should run... ideally I want to deny direct access to the file.

---

### Post by Lars Noodén on 2009-10-13
Put it in a subfolder, for example under cgi-bin, but can be anywhere ever one of your ScriptAlias points to.  Then use the <Directory> directive to put it behind a password.  For example:

```

        <Directory "/usr/lib/cgi-bin/stream/">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order deny,allow
                Deny from all
                AuthType Basic
                AuthName "Streamer Password Required"
                AuthUserFile  /var/apache/passwords/streamer.password.file
                AuthGroupFile /var/apache/passwords/streamer.group.file
                Require Group streamers 
        </Directory>

```

If you have a lot of users you can look at mod_authn_dbm or even mod_auth_mysql or mod_auth_postgresql instead of mod_auth_basic.  (There should also be a way to kerberize the login, but I don't remember it.)

Prepare the password and group files
```

mkdir -p /var/apache/passwords/
chgrp www-data /var/apache/passwords/
chmod 0751 /var/apache/
chmod 0751 /var/apache/passwords/
chmod 0660 /var/apache/passwords/streamer.group.file
chmod 0660 /var/apache/passwords/streamer.password.file
chgrp www-data /var/apache/passwords/streamer.group.file
chgrp www-data /var/apache/passwords/streamer.password.file

```

```

htpasswd -c /var/apache/passwords/streamer.password.file streamguest
echo "streamers: streamguest" > /var/apache/passwords/streamer.group.file

```

---

### Post by weirdbeardmt on 2009-10-14
That's great, thanks. Will try it this weekend.

---

