---
title: "wget and php password"
date: 2008-02-02
forum: Server Platforms
---

### Post by Marinodimare on 2008-02-02
HI, 

I have to download a lot of small documents from my friend's site, and to save me a lot if work, I'd like wget to it for me. The problem is that the site is made by php, and it has a logon. Whenever I try to download a file wget will give me the warning '302 encountered' and just gets the 'logon.php' file. Is it possible to use wget or anything else to get files from a php password protected server? I've tried the --user=user and --password=password option.

---

### Post by scxtt on 2008-02-02
check out curl

i was able to do:

curl <url> -u $USER_NAME

and have it pull down a site restricted w/ htaccess ...

looking at the man page, it seems you can pass PHP form data too ...

---

### Post by Marinodimare on 2008-02-02
It seems to be connecting, but it's not downloading anything. Also, no message is printed to my screen after entering the password. Any ideas why?

---

### Post by scxtt on 2008-02-02
can you be more specific about what you're doing?

i'm not sure what it'll do if there's a login.php page that's basically a redirector ...

---

### Post by Marinodimare on 2008-02-03
This is a print from the terminal:
```

$curl -u marino -o winner_59 http://www.example.nl/marino/files.php?winner=59
Enter host password for user 'marino':
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
$

```
And then ..nothing is downloaded

---

### Post by scxtt on 2008-02-04
maybe the **-F** option will help?

$curl -u marino -o winner_59 -F "winner=59" [http://www.example.nl/marino/files.php](http://www.example.nl/marino/files.php)

---

