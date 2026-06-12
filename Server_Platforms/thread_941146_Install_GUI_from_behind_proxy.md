---
title: "Install GUI from behind proxy"
date: 2008-10-07
forum: Server Platforms
---

### Post by computer_freak_8 on 2008-10-07
Hello, 

I have just installed Ubuntu Server 8.04.1 LTS on one of the servers at my school. I need to install the GUI, but I am behind a proxy.

I set the proxy in my /etc/bash.bashrc, file (or whatever it was - I'm not there now; I'm going from memory,) but I get errors when I try to connect to the proxy. The proxy requires a password. So, after setting it in the mentioned file I ran
"export http_proxy=http://username:password@proxy.server.url.here:port/", substituting in the correct information for my situation.

I ran "sudo apt-get update" but got an error, I believe it was 407, but I know it was something like "the proxy requires authentication". 

I'm confused because I thought that that was what the "username:password" part did. 

Any ideas, anyone?


Thanks,
computer_freak_8

---

### Post by werries on 2008-10-07
Why not just manage it from terminal?
The GUI would take more system resources.

---

### Post by computer_freak_8 on 2008-10-07
> **werries said:**
> Why not just manage it from terminal?
The GUI would take more system resources.

Yes, I am aware of this. 

It's a long story. We need this to be usable as a desktop as well as a server. There are people from "somewhat new" to "very new" to Linux that will be learning how to use/manage a Linux server. 

We want them to learn in small steps. Once they get used to the settings of the GUI, we well move them to a CLI.

Do you know how to install it?

---

### Post by werries on 2008-10-08
I only know of "sudo apt-get install ubuntu-desktop". that would install the GUI. I don't have any experience with proxies though. =/

---

### Post by lykwydchykyn on 2008-10-08
Is it a microsoft proxy by chance, authenticating against an Active Directory?

---

### Post by computer_freak_8 on 2008-10-08
> **lykwydchykyn said:**
> Is it a microsoft proxy by chance, authenticating against an Active Directory?

I'm almost positive it's a Microsoft proxy, but I don't know about the "Active Directory" part. It's possible, though, I'm sure.

---

### Post by lykwydchykyn on 2008-10-08
If it's a microsoft proxy, you might need to add in the domain name, e.g.:
```

export http_proxy="http://domain\username:password@proxy.server.url.here:port"

```

---

### Post by computer_freak_8 on 2008-10-08
> **lykwydchykyn said:**
> If it's a microsoft proxy, you might need to add in the domain name, e.g.:
```

export http_proxy="http://domain\username:password@proxy.server.url.here:port"

```

Thanks, but it didn't work. I tried each of the following (one at a time, of course):
```
export http_proxy=http://DOMAIN\\username:password@proxy.server.url.here:80/

export http_proxy=http://DOMAIN\username:password@proxy.server.url.here:80/

export http_proxy=http://DOMAIN\\username:password@proxy.server.url.here:80

export http_proxy=http://DOMAIN\username:password@proxy.server.url.here:80
```

---

### Post by computer_freak_8 on 2008-10-08
Alright, I got the proxy working using one of the comments at [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html]("http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html")

Now, when I run "sudo apt-get update", I get a 401 Unauthorized error.

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Filename.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Filename.gz) 401 Unauthorized [IP: 192.168.xxx.xxx 80]

The IP address is that of my proxy. (I changed the last two octets for security reasons.)

So, the Ubuntu repositories don't like my proxy??? What's up with that? What's(/What am I doing) wrong?


Thanks so much,
computer_freak_8

---

### Post by lykwydchykyn on 2008-10-08
Sounds more like the proxy is blocking .gz files to me; the 401 is coming from your proxy, not the repo server.  Have you talked to the network admin about this?  What kind of filtering rules do they have in place?

---

### Post by promodus on 2008-10-09
```
echo "Acquire::http::Proxy \"http://domain\username:password@proxy.server.url.here:port\"" > /etc/apt/apt.conf
```

---

### Post by computer_freak_8 on 2008-10-10
> **promodus said:**
> ```
echo "Acquire::http::Proxy \"http://domain\username:password@proxy.server.url.here:port\"" > /etc/apt/apt.conf
```

Is there a way to do this without storing the password in the file?

I am a bit concerned about security...

---

### Post by computer_freak_8 on 2008-10-10
lykwydchykyn: Thanks for the information; all that I know it that our teacher said that it was Ubuntu not liking our proxy.

promodus: Although I am still concerned about security, I tried your idea and got an error:

> E: Syntax error /etc/apt/apt.conf:2: Extra junk at end of file

---

### Post by computer_freak_8 on 2008-10-10
promodus: According to the page [here]("http://linux.die.net/man/5/apt.conf"), > The ***http_proxy*** environment variable will override all settings.

Therefore, I do not need it in my apt.conf file, although I did find how to put it in there, see [here]("http://www.linuxquestions.org/questions/fedora-35/how-to-set-up-proxy-in-apt-gets-apt.conf-265793/").

Anyhow, I decided to bypass the proxy using my Sprint card, which I use for my connection at home. However, even though it is the same operating system, I get errors like this:
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)


Note: Yes, I disabled the proxy settings I had previously set, so this isn't the problem - *_unless_* Ubuntu stores the proxy configuration given at install time in a file that I am not aware of. Does anyone know where this file is?

---

### Post by koenn on 2008-10-10
> **computer_freak_8 said:**
> 
Note: Yes, I disabled the proxy settings I had previously set, so this isn't the problem - *_unless_* Ubuntu stores the proxy configuration given at install time in a file that I am not aware of. Does anyone know where this file is?
it does, actually : it creates /etc/apt/sources.list and .../apt.conf according to info you input during install - si if those files are OK you shouldn't have a problem.

You can check by running this in a terminal :
```
watch netstat -an
```
Then, browse to a couple of web sites and see that you're going through a proxy. Here you see me refreshing a couple of tabs in firefox.
```

tcp        0      0 192.168.11.251:36445     192.168.25.1:3128        ESTABLISHED
tcp        0      0 192.168.11.251:36450     192.168.25.1:3128        ESTABLISHED
tcp        0      0 192.168.11.251:36451     192.168.25.1:3128        ESTABLISHED
tcp        0      0 192.168.11.251:36443     192.168.25.1:3128        ESTABLISHED
tcp        0      0 192.168.11.251:36447     192.168.25.1:3128        ESTABLISHED
```

Then run apt and see if the connection goes straight to the repo servers, or to the proxy

---

### Post by computer_freak_8 on 2008-10-10
koenn:

Thanks for the tips. I will have to wait until Monday to try it, however.

About those two files:
1. I thought the sources file simply defined where to find the packages at, but I will still check on Monday.
2. The configuration file was blank before I edited it, and that is how it is now.


Where would the file be that contains the "system"/"global" proxy settings - not just those for Apt?

---

### Post by promodus on 2008-10-10
> **computer_freak_8 said:**
> lykwydchykyn: Thanks for the information; all that I know it that our teacher said that it was Ubuntu not liking our proxy.

promodus: Although I am still concerned about security, I tried your idea and got an error:

My mistake, there should be a semicolon!
```
echo "Acquire::http::Proxy \"http://domain\username:password@proxy.server.url.here:port\";" > /etc/apt/apt.conf
```

---

### Post by koenn on 2008-10-10
> **computer_freak_8 said:**
> 
1. I thought the sources file simply defined where to find the packages at, but I will still check on Monday.

I meant that, during install, the installer configures the package manager, i.e. it creates sources.list to know what repos to use, and creates apt.conf to know of any peculiarities such as proxy settings, so yes, you should only check apt.conf for proxy settings.


You could also check environment settings (command: env)

edit:
you did blank or unset the http_proxy variable, didn't you ?

---

### Post by computer_freak_8 on 2008-10-10
> **koenn said:**
> 
edit:
you did blank or unset the http_proxy variable, didn't you ?

No! I thought that maybe by logging out, it would reset itself. How do I do this?

Okay, first, I have to guess. Here are my guesses:
```
/dev/null > http_proxy

http_proxy < /dev/null

export http_proxy=/dev/null

export http_proxy=$/dev/null

export http_proxy="/dev/null"

export http_proxy="$/dev/null"
```

Would any of these work? (My newbie-ness is almost certainly showing...)


Thanks,
computer_freak_8

---

### Post by lykwydchykyn on 2008-10-10
try:
```

unset http_proxy

```

---

### Post by koenn on 2008-10-11
> **lykwydchykyn said:**
> 
```

unset http_proxy

```
that should do it

> **computer_freak_8 said:**
> No! I thought that maybe by logging out, it would reset itself. How do I do this?

Okay, first, I have to guess. Here are my guesses:
```
/dev/null > http_proxy

http_proxy < /dev/null

export http_proxy=/dev/null

export http_proxy=$/dev/null

export http_proxy="/dev/null"

export http_proxy="$/dev/null"
```

Would any of these work? (My newbie-ness is almost certainly showing...)


Thanks,
computer_freak_8

nice try.
something like```
export http_proxy=""
```would actually have worked.

---

### Post by computer_freak_8 on 2008-10-11
lykwydchykyn and koenn:

Thanks for that. I figured something might be wrong with my syntax...

As I mentioned in another post in this thread, I will (unfortunately) have to wait until Monday to try this. I really do appreciate the quick responses, though. The more information I'm armed with, the better. At least as I figure it, this way I will have a few different ways to try, and if for some reason they don't work, we can move on with troubleshooting more quickly.


Thanks again,
computer_freak_8

---

### Post by computer_freak_8 on 2008-10-13
Alright, I unset the http_proxy environmental variable and it still didn't work. 

So, I would like to try and get the proxy going (as was my original goal) and then ditch the Sprint card efforts, since it won't always be there, anyways.

promodus:
Is there any way to use your code without entering the username and password?

I can put the following code into my /etc/bash.bashrc file...
```
function proxy(){
echo -n "username:"
read -e username
echo -n "password:"
read -es password
export http_proxy="http://$username:$password@192.168.xx.xx:80/"
export ftp_proxy="http://$username:$password@192.168.xx.xx:80/"
echo -e "\nProxy environmental variables set."
}
```
...and type "proxy" (without quotes) in a terminal, and it will prompt me for my username and password. So, can I simply substitute ...$username:$password@... where your code shows ...username:password... and have it work correctly?

Also, I found this code somewhere (can't remember where) to put in /apt/apt.conf to setup the proxy:
```
Acquire {
Retries "0";
HTTP {
Proxy "http://proxy.url.here:80";
};
};
```
Can I sub in "$username:$password@" directly before the "proxy.url.here" and have it work?


Thanks in advance, 
computer_freak_8

---

### Post by koenn on 2008-10-13
yes for both questions;
it's usually not considerd good practice to put passwords in scripts like that, but if you want it that way ..

/apt/apt.conf - probably /etc/apt/apt.conf; and I thought this was already meantioned somewhere in this thread ...

edit : OK, slightly different syntax

---

### Post by computer_freak_8 on 2008-10-13
> **koenn said:**
> /apt/apt.conf - probably /etc/apt/apt.conf; and I thought this was already meantioned somewhere in this thread ...

edit : OK, slightly different syntax

Yes, I meant /etc/apt/apt.conf, not /apt/apt.conf.

I tried several different things, including exporting the username and password to the respective variables, and I even tried taking out the whole "http://........:80/" and putting in "$http_proxy" instead; still no luck, same 401 error.

I know it is exporting because I checked it with "echo $http_proxy", "echo $username", et cetera.

---

### Post by computer_freak_8 on 2008-10-23
Don't know if this will help anyone to troubleshoot with me, but I noticed something interesting.

"wget http://us.archive.ubuntu.com/blocked/file/path/here.gz" gives a 407 error. However, I can easily download it from Firefox. 

Any ideas as to why this is? Can I make my terminal appear (to the proxy) to be Firefox? If so, how do I do this?


Thanks in advance,
computer_freak_8

---

### Post by koenn on 2008-10-23
> **computer_freak_8 said:**
> Don't know if this will help anyone to troubleshoot with me, but I noticed something interesting.

"wget http://us.archive.ubuntu.com/blocked/file/path/here.gz" gives a 407 error. However, I can easily download it from Firefox. 

Any ideas as to why this is? Can I make my terminal appear (to the proxy) to be Firefox? If so, how do I do this?


Thanks in advance,
computer_freak_8
most likely because FF is configured to use a proxy, wget isn't, and you can't get direct internet access because of a firewall somewhere.

wget has an option to set a proxy (man wget for syntax), you could see if that helps.

---

### Post by computer_freak_8 on 2008-11-01
> **koenn said:**
> most likely because FF is configured to use a proxy, wget isn't, and you can't get direct internet access because of a firewall somewhere.

wget has an option to set a proxy (man wget for syntax), you could see if that helps.

Thanks for that, but I'm still confused then: I have configured the environmental variable "http_proxy" as well as "/etc/apt/apt.conf", and it still won't use a proxy - just like wget won't.

I mean, it makes sense for wget to be giving me errors (if it doesn't see "http_proxy"), but it doesn't make sense for apt-get to be giving me errors. 

Yes, Firefox is configured to use a proxy. I had to go into "Edit" --> "Preferences" to make it that way. How do I get my CLI programs to use the proxy? 

Now, it's obvious that my proxy doesn't block the packages; they go through just fine in Firefox. So it is something with the authentication. (I think.) 

Is there some way to get the CLI programs - especially apt-get - to prompt me for my authentication as needed, like Firefox does? Maybe this would solve my problem...

---

