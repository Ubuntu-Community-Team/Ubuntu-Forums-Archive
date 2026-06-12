---
title: "Ubuntu server in VBox issues"
date: 2010-08-07
forum: Server Platforms
---

### Post by OxentroT on 2010-08-07
This is my first server installation. I am intending to make this a basic web server for educational purposes. I have installed this server in VirtualBox, everything seemed to go fine besides the fact that I accidentally hit the enter button when I was at the opportunity to install the additional software during the initial setup. I figured that it was no big deal as I could just use aptitude to get what I needed later. My first step was to get LAMP setup.

Heres where it started to seem to go wrong: I installed Apache2, however, it seems that I am unable to test it (no browser).
```

oliver@DrDoak:~$http://localhost/
-bash: http://localhost/: No such file or directory
oliver@DrDoak:~$

``` 


I then proceeded to install php5 again I have ran into trouble when trying to open through GEDIT.
```

oliver@DrDoak:~$ sudo gedit /var/www/testphp.php
sudo: gedit: command not found
oliver@DrDoak:~$

```

I am thankful for any information in solving this issue.

---

### Post by Bachstelze on 2010-08-07
If you want a command-line browser, you can use links:

```
sudo apt-get install links
links http://localhost
```

Or you can just test it from the host system

---

### Post by CharlesA on 2010-08-07
> **Bachstelze said:**
> If you want a command-line browser, you can use links:

```
sudo apt-get install links
links http://localhost
```

Or you can just test it from the host system

This would work.

---

### Post by Bachstelze on 2010-08-07
> **CharlesA said:**
> This would work.

Thank you. ;)

---

### Post by OxentroT on 2010-08-08
>  Originally Posted by Bachstelze  View Post
If you want a command-line browser, you can use links:

Code:

sudo apt-get install links
links [http://localhost](http://localhost)

Or you can just test it from the host system

Worked like a charm! 

Rock On!

:guitar:

---

