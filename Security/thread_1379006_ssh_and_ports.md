---
title: "ssh and ports"
date: 2010-01-12
forum: Security
---

### Post by cucuru on 2010-01-12
hello, I have to connect with ssh different ports in the same computer, I have too many, and is very confusing use the numbers, so I would like call them with a name, but I'm not sure it is possible or I'm doing something wrong:

In /etc/services I wrote this:

```

ssh2    8888/tcp     2ssh

```

Save and anything else.

but when I put:

```

ssh -p 2ssh xx.xx.xx.xx
Bad port '2ssh'

```

The 8888 port is enabled in the server, the number has no problem.

I read that -p [numerical_port], but I didn't find any other option with a name instead of number.

Is it possible what I want to do?

Thank you. Regards.

---

### Post by ajmorris on 2010-01-12
hi there,
as you have noticed, that will simply not work. the -p parameter on the ssh application requires a numerical port, and not something defined in /etc/services. 
As it happens /etc/services doesnt function the way you expected it to, that file is more like a "phonebook" for linux, and only lists the services that a linux machine *may* have to offer, for example, if you install the 'nmap' package, this will increase the number of services listed in the "phonebook".

To do what you are trying to accomplish, i would recommend more of an alias approach, i.e aliasing multiple variables to achieve various ssh connections.

To do this, open up ~/.bashrc (whilst dash is the default shell in ubuntu, dash supports the bashrc file) in your favourite text editor. Then add the following to your bashrc script:
 ```
alias ssh2='ssh -p 8888 user@server' 
```This will create an alias in your bash/dash shell for ssh2, so if you type ssh2 into your terminal, it will run the command "ssh -p 8888 user@server".

If you are not using dash/bash, this alias command will most likely work for your shell, however, it may not.

Whilst you can also alias ssh2 to a number in your bashrc, you cannot use 'ssh2' on the -p paramater on the ssh command, as ssh's syntax will not allow it. As for running ssh with a text variable for the port, afaik its not possible, if it is, i'd be interested to know how :)

AJ

---

### Post by cucuru on 2010-01-12
Thank you for your explanation, it is really good!

it works!

Regards

---

