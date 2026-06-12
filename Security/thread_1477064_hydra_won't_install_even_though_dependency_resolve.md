---
title: "hydra won't install even though dependency resolved"
date: 2010-05-08
forum: Security
---

### Post by gregnorc on 2010-05-08
So I'm trying to install hydra 5.4, but whenever I go to make, I get the following error:

```
~/bin/hydra-5.4-src$ make
gcc -I. -Wall -O2 -c hydra-ssh2.c -DLIBOPENSSL -DLIBSSH 
hydra-ssh2.c:10:2: warning: #warning "If compilation of hydra-ssh2 fails, you are not using v0.11. Download from http://www.0xbadc0de.be/"
hydra-ssh2.c: In function ‘start_ssh2’:
hydra-ssh2.c:24: error: ‘SSH_SESSION’ undeclared (first use in this function)
hydra-ssh2.c:24: error: (Each undeclared identifier is reported only once
hydra-ssh2.c:24: error: for each function it appears in.)
hydra-ssh2.c:24: error: expected expression before ‘ssh_session’
hydra-ssh2.c:25: error: ‘SSH_OPTIONS’ undeclared (first use in this function)
hydra-ssh2.c:25: error: ‘ssh_opt’ undeclared (first use in this function)
hydra-ssh2.c:34: warning: implicit declaration of function ‘options_new’
hydra-ssh2.c:44: warning: implicit declaration of function ‘options_set_wanted_method’
hydra-ssh2.c:44: error: ‘KEX_COMP_C_S’ undeclared (first use in this function)
hydra-ssh2.c:45: error: ‘KEX_COMP_S_C’ undeclared (first use in this function)
hydra-ssh2.c:46: warning: implicit declaration of function ‘options_set_port’
hydra-ssh2.c:47: warning: implicit declaration of function ‘options_set_host’
hydra-ssh2.c:48: warning: implicit declaration of function ‘options_set_username’
hydra-ssh2.c:50: error: expected ‘)’ before ‘=’ token
hydra-ssh2.c:50: error: expected expression before ‘==’ token
hydra-ssh2.c:51: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: warning: left-hand operand of comma expression has no effect
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: warning: left-hand operand of comma expression has no effect
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:53: error: expected expression before ‘ssh_session’
hydra-ssh2.c:66: error: expected expression before ‘ssh_session’
hydra-ssh2.c:66: error: too few arguments to function ‘ssh_userauth_kbdint’
hydra-ssh2.c:68: error: expected expression before ‘ssh_session’
hydra-ssh2.c:68: error: too few arguments to function ‘ssh_userauth_kbdint_setanswer’
hydra-ssh2.c:69: error: expected expression before ‘ssh_session’
hydra-ssh2.c:69: error: too few arguments to function ‘ssh_userauth_kbdint’
hydra-ssh2.c:73: error: expected expression before ‘ssh_session’
hydra-ssh2.c:73: error: too few arguments to function ‘ssh_userauth_password’
hydra-ssh2.c:74: error: expected expression before ‘ssh_session’
hydra-ssh2.c:82: warning: implicit declaration of function ‘ssh_error_code’
hydra-ssh2.c:82: error: expected expression before ‘ssh_session’
hydra-ssh2.c:87: error: expected expression before ‘ssh_session’
make: *** [hydra-ssh2.o] Error 1

``` 

I went to the link mentioned, not only is that version of libssh not available, it's horribly out of date. I did an apt-get to get the latest libsshh, libssh-dev, etc...

I'm running 10.04... (Linux wopr 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux)

Any ideas are appreciated, this is a pretty popular tool, I'm guessing someone had found a workaround? It doesn't seem to be available via apt-get so source is the only option unfortunately...

---

### Post by Dexi on 2010-08-16
Same exact problem... :(

---

### Post by bodhi.zazen on 2010-08-17
Since you are compiling from source code, you should post to the hydra mailing list.

You can also try google

[http://wiredbytes.com/node/23](http://wiredbytes.com/node/23)

---

