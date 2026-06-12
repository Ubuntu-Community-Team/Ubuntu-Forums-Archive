---
title: "Security when running ssh and apache."
date: 2006-11-14
forum: Server Platforms
---

### Post by Ramses de Norre on 2006-11-14
I have a question about security: I have a normal desktop but I like to run apache and ssh on it so that I can log in remotely and host files on my pc for the time it's turned on.

But I wondered how safe this is? I'm not using the default ports, I've configured two other ports for ssh and apache (above 10000), I disabled root access through ssh and I'm running denyhost (with very restrictive settings), I've also got a pretty strong password I think.

Apache is plain apache1.3 with php5 (never tried apache2 because I already know apache1.3...).

I've configured firestarter to accept all hosts on the ports apache and ssh listen on, so that I can log on from everywhere and watch my hosted files from everywhere.

All thoughts about the consequences of these services are welcome, I'm just worried about hackers or stuff like that..

---

### Post by skymt on 2006-11-14
Apache is mostly safe if you serve static content. If you have a security hole, it will most likely be in your PHP code, so be careful there. There have been security vulnerabilities in Apache that didn't have to do with dynamic content, but they're patched quickly.

PHP has a bad track record for security. You may want to look into a web framework (Ruby on Rails, Django) or plain CGI.

For SSH, a strong password should be enough. If you want extra security, generate a key pair and disable password login. See "Public key authentication" in the [SSHHowto](https://help.ubuntu.com/community/SSHHowto).

---

