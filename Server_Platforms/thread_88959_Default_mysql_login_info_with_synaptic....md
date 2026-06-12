---
title: "Default mysql login info with synaptic..."
date: 2005-11-11
forum: Server Platforms
---

### Post by Todd_Z on 2005-11-11
I installed php5/apache2/mysql with synaptic, but when i install phpmyadmin and it asks me for my login information - i dont know what that information is... is there a default login for mysql?

I know that root and no password works, but is there a specific mysql user? Or do I need to make one? Or do i not need to?

---

### Post by HunterCo on 2005-11-20
[QUOTE=Todd_Z]I know that root and no password works, but is there a specific mysql user? Or do I need to make one? Or do i not need to?[/QUOTE]
I'm sure you've already figured this one out over the course of a week, but in case not I thought I'd throw in my 2 cents...

When you log in the first time, use the root username with no password. On the summary page you're viewing, there with be 2 columns (not counting the sidebar) labeled MySQL and phpMyAdmin. Under the MySQL, you'll find a clickable link for priviledges. In there, you can add users with or without passwords, change the root password, etc. Keep in mind, most of the changes you make will be MySQL specific, and won't change the account info of the actual Ubuntu server system.

---

