---
title: "How to build the sweetest linux box ever."
date: 2013-05-29
forum: Tutorials
---

### Post by ki4jgt on 2013-05-29
So, I've been wondering what does my computer need recently. Like always I install Tor and an SSH server on every computer I get and then configure the server to only accept connections from Tor at a specified hidden address. Thought that would come in handy if my laptop was ever lost or stolen. I've been reading though about routing your HTTP requests through your ssh server. I decided to give this a try. I haven't officially tried it on another machine yet but it would be something to setup on a VPS. Seeing the benefits of Tor, this would give you access to your laptop or server no matter where you were on the planet and also give you secured internet no matter where you go, without having to pay for a VPN or Proxy service (if the tutorials were correct).

First, the prerequisites:

```

$ sudo apt-get install tor ssh

```

Next, we need to configure our tor hidden service. This is a URL given to you by the Tor program which will be linked to your computer/server no matter where you are. I prefer a graphical layout of things as it's just easier so:

```

$ sudo nautilus

```

We are going to go looking for our Torc file located in /etc/tor/torcc.

Under this section:
```

############### This section is just for location-hidden services ###

```

You will find these lines:

```

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80

```

Change them to:

```

HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 22 127.0.0.1:22

```

Close the file and save it.

Next you need to restart Tor. Issue the following commands.

```

$ sudo /etc/init.d/tor stop
$ sudo /etc/init.d/tor start

```

With your rooted nautilus still open, navigate to /var/lib/tor/hidden_service/ and open a file called hostname and copy it's contents to your clipboard. Be sure to paste it in a safe place as it's what uniquely identifies your device in the Tor network.

Next, open:

```

/etc/ssh/sshd_config

```

and search for the following,

```

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0

```

Replace the last line with,
```

ListenAddress 0.0.0.0

```

Close and save. You may now close your rooted nautilus session as well. Simply run the following:
```

$ sudo reload ssh

```

and you're setup. You may now ssh into your laptop/server at any time with the following command from any linux box that has tor installed (or windows box using putty).

```

$ torify ssh user@hostname

```

Replace user with your Linux username and hostname with the hostname you copied earlier. The password will be your linux password. To utilize this device's internet connection as a proxy on another linux box (IE, at a coffee shop or similar where you would like to secure your connection) simply type:

```

$ torify ssh -D port -C user@hostname

```

Replace port with the port of the sock5 proxy you wish to run on your local machine.

Any questions/comments are welcome.

---

