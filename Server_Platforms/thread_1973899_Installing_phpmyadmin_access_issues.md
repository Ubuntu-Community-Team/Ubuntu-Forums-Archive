---
title: "Installing phpmyadmin access issues"
date: 2012-05-05
forum: Server Platforms
---

### Post by Chris Psycho on 2012-05-05
[SIZE=2]Hi there. I'm running Ubuntu 11.10

I'm having trouble installing or accessing phpmyadmin on my localhost.[/SIZE] [SIZE=2]

I successfully 'installed' it and went through the 'database daemon configuration'. However when I try to access localhost/phpmyadmin I get a " [/SIZE][SIZE=2] Not Found[/SIZE][SIZE=1][SIZE=2]. The requested URL /phpmyadmin was not found on this server."

I have run though the installation a few times as I read I might have not selected 'apache2' as the server, but this does not seem to be the problem.

Ideas?[/SIZE]
[/SIZE]

---

### Post by Chris Psycho on 2012-05-05
Woot woot I think I may have solved it.

I ran the following command "sudo ln -s /usr/share/phpmyadmin /var/www " which seems to have put a shortcut in /var/www. 

Is there any security issues with this? It is connected to the internet.

---

