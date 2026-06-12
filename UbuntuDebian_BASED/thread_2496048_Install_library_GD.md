---
title: "Install library GD"
date: 2024-03-12
forum: Ubuntu/Debian BASED
---

### Post by franjgg on 2024-03-12
Hello,

Well, I'm trying to install the GD library to convert images from PHP, the thing is that I have tried several ways and nothing.

I have Ubuntu 16.04 with PHP 7.4.13, so I don't have much knowledge with bash.

I have tried to install it this way:

sudo apt-get update
sudo apt-get install php7.4-gd
sudo systemctl restart apache2
apache2 service restart

I get this response:

unable to locate package php7.4-gd
couldn't find any package by glog 
couldn't find any package by regex

I read that I should update the repository or add the appropriate one, and I tried:

sudo apt-add-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install -y php7.4-gd

But yes with the same result.

He also tried installing the php7.0-gd version but nothing.

Let's see if someone can guide me a little, I have done everything from a vnc connection and being root.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293485&stc=1[/IMG]

---

### Post by Bashing-om on 2024-03-12
franjgg - unGood :(

As release 16.04 is long past End_Of_Life. The software repo no longer exists.
You are strongly advised to update to a current release.

22.04 - jammy - has php8.1-gd available.

[INDENT][INDENT]all things come to an end
[/INDENT][/INDENT]

---

### Post by franjgg on 2024-03-13
Hi, thanks for your response.

  I have a bit of new information, typed the command: apt search php-dg  

And apparently it shows that it is installed as seen in the image, but it does not appear in the phpinfo.php file, and I cannot use it either in php it does not work.  

I don't know what it could be.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293486&stc=1[/IMG]

---

