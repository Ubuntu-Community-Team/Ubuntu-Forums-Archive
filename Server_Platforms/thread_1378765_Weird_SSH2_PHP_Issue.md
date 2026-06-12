---
title: "Weird SSH2 PHP Issue"
date: 2010-01-11
forum: Server Platforms
---

### Post by Jason Giedymin on 2010-01-11
I'm having an issue with SSH2 lib (0.11) for PHP.  Can't find the reason anywhere.  Thought I'd pose the question here.

Given:
[LIST]
[*]Ubuntu Karmic.
[*]sshd config set to accept password.
[*]user with password set.
[*]ssh is listening, checked via netstat
[*]running ssh I can log in fine
[*]running ssh_exec i can execute a script to echo into a file i choose
[/LIST]

The issue: I get timeouts on the stream, and can't read it.  Even though the commands execute.

What could possibly be the reason why?

---

### Post by Jason Giedymin on 2010-01-14
Update: Ditched PHP-SSH (v0.11) , moved on to PHPSECLIB.

Even when working it wasn't 100% (PHP-SSH2).

---

