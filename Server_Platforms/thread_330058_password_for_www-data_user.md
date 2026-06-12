---
title: "password for www-data user"
date: 2007-01-02
forum: Server Platforms
---

### Post by gnel on 2007-01-02
Hi, I'm trying to execute a script as www-data user so I'm firstly doing a 'su www-data' but it ask me password but I don't know what password does ubuntu put to that user..(I tried empty password with no luck)... I'm doing this because I'm following this[1] instructions to debug a problem in my subversion script...

[1] [http://subversion.tigris.org/faq.html#hook-debugging](http://subversion.tigris.org/faq.html#hook-debugging)

---

### Post by linuchsan on 2007-01-02
you can edit /etc/sudoers with the line:

www-data ALL=(ALL) NOPASSWD:ALL

---

### Post by bernied on 2007-01-02
The password is probably stored in the /etc/shadow file (encrypted):
```
sudo cat /etc/shadow | grep www-data
```
From 'man shadow':
> If the password field contains some string that is not valid result of
crypt(3), for instance ! or *, the user will not be able to use a unix
password to log in,
...So you can take a copy of the file, create a password for the user using passwd, do what you need to do, then revert the file to its original state:
```
sudo cp /etc/shadow /etc/shadow.backup
sudo passwd www-data    # the first password needed is yours (for sudo), then repeat your new www-data password twice
[do your thing now]
sudo cp /etc/shadow.backup /etc/shadow
```

---

### Post by bernied on 2007-01-02
Of course if linuchsan's solution works, then it is much easier

---

### Post by gnel on 2007-01-04
Thanks, Linuchsan's solution worked very well, I just now have to do 'sudo -u www-data anycommand' to run anycommand as www-data user... so I've now created my svn repository as www-data user to not have more problems with permissions in svn through apache:

 sudo -u www-data svnadmin create --fs-type fsfs /var/local/svn/repositorio

Thanks again...;)

---

