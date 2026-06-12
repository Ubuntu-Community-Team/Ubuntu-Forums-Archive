---
title: "SSH Port Forwarding and chroot"
date: 2009-03-14
forum: Server Platforms
---

### Post by mogliii on 2009-03-14
Hi,

To breakdown the question: What is necessary in a chroot environment, to allow port forwarding to the host (outside chroot).

The Scenario: I have a sshd running. I setup one user to be jailed in a chroot when loggin in via sftp or ssh. I use putty to connect and also portforwarding (5500 for VNC). The shell is restricted (can not browse the file system).

However, when I then start an vnc server on the remote client, the debug of ssh shows:
```
debug1: server_input_channel_open: ctype direct-tcpip rchan 257 win 16384 max 16384
debug1: server_request_direct_tcpip: originator 0.0.0.0 port 0, target 127.0.0.0 port 5500
debug1: connect_next: host 127.0.0.0 ([127.0.0.0]:5500): Network is unreachable
connect to 127.0.0.0 port 5500 failed: Network is unreachable
debug1: server_input_channel_open: failure direct-tcpip

```

I have already copied /etc/hosts to the chroot (before localhost could not be resolved).

As I can connect to the vnc when I login on ssh with normal user account (no chroot), it must be something with the chroot. Is there some means in linux to have a port-forwarding to the host?

Any help appreciated. I feel so close to setting up my secure helpdesk  :popcorn:

---

### Post by HermanAB on 2009-03-14
Well, if you have SSH working, why do you bother with VNC?

$ ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

### Post by mogliii on 2009-03-14
Hi,

what I want to ultimatively do is described here (though in German) but with additional ssh 
[[COLOR="Red"]Reverse VNC Helpdesk[/COLOR]]("http://christoph-langner.de/2009/01/das-eigene-pc-helpdesk/")

You setup sshd and start vncviewer in listen mode, and somebody else (e.g. Win) starts the custom generated .exe, which will allow the vncviewer to see the clients desktop.

The advantage: The other person does not need to worry about port forwarding on the router. And if I am at a computer without port-forwarding, I can vnc into the server, and have the client connected to the server, so two computers can share the desktop without any of them having port forwarding (see also TeamViewer).
And everything over ssh.

But not to compromise my server security by giving ssh login-credentials to anyone, I want to create this jailed ssh account.

Therefore your solution might not be what I am looking for. But thank you for your idea.

---

