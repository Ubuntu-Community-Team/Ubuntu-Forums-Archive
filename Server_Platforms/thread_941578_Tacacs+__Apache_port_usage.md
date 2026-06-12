---
title: "Tacacs+ / Apache port usage"
date: 2008-10-08
forum: Server Platforms
---

### Post by mscoxoh on 2008-10-08
(I'm not sure if this is the right forum since my question covers a few possibilities. I apologize if I'm in the wrong place.)

My end goal is to install Tacacs+ on my Ubuntu (7.10 Gutsy) server. I was using the instructions located below with decent success.

[http://tacacs-plus.rubyforge.org/howto/tacacs_plus_controller_install.html](http://tacacs-plus.rubyforge.org/howto/tacacs_plus_controller_install.html)

I also have Squid+Dansguardian running on this box. During the above procedure, when I tried to start Apache2, I received this error:

(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
   ...fail!

My guess is that Squid+DansG is already listening on this port (as well as 80)? Can the two co-exist? Can I use Apache on a different port, and how, or is there a better way to go about this? (I tried modifying /etc/apache2/ports.conf with Listen=444 for kicks & grins; Apache starts, but not sure if that's all I need - [http://1.1.1.1:444](http://1.1.1.1:444) doesn't work, either does straight [http://1.1.1.1](http://1.1.1.1))

Also, I understand I need to "remember to configure your daemons to listen on port 4949 instead of the default port of 49." Is that just the tacacs daemon? How do I change the port it listens to?

Thanks for any assistance.

.m.

---

