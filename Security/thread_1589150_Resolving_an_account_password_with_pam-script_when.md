---
title: "Resolving an account password with pam-script when using passwordless SSH. Possible?"
date: 2010-10-06
forum: Security
---

### Post by mattp52 on 2010-10-06
Hi there,

I'm trying to configure a process triggered by an SVN post-commit hook which will log into a different host and carry out an SVN update on a file path on that host before exiting. An earlier attempt mounted the remote filepath on the SVN host using sshfs and performed the update locally. This worked but it was incredibly slow (minutes to complete an SVN update). 

So, Plan B was to set-up a passwordless login for the user the script runs as and then use pam-script to script a checkout from a repository using the same credentials. The problem is, passwordless SSH login using private/public keys appears to bypass the PAM authentication system or at least interact with it in a way that no environment variables (including the SSH user's name and pass) are resolved by the authentication script being used by pam-script.

I've tested the pam-script behaviour for normal log-ins and it exposes these variables fine. This leaves me in a Catch-22 with trying to script access on one host to perform actions on another while avoiding user/pass prompts or the need to store plaintext passwords on the remote host.

Anyone know if there's a way to resolve a user account password via PAM when using passwordless SSH or, another approach I could take to perform scripted  tasks on the remote system requiring authentication? Ideally without storing the passwords on the remote system (at least in unencrypted form).

Thanks.

---

### Post by bodhi.zazen on 2010-10-06
Use svn+ssh plus keys.

See this blog

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

---

