---
title: "SSH and authorized_keys maintenance"
date: 2008-09-05
forum: Server Platforms
---

### Post by jpdk on 2008-09-05
Hi Guys,

I have a few questions. I have worked a little bit with Linux as a user, but I have just recently sete up my first Linux Server. 

My reason for doing this is that I need to share a MySql database with my clients.

So I downloaded the latest release of Ubuntu Server 8.04, and set it up (easy) ;)

Since this server is going to be outside my firewall, I have installed Firestarter and closed down everything so no ports are open and no ping is replied to.

But I still need my MySql to be accessible. So I opened up port 22 and set up sshd to only accept certificate authentication. This works well. I have set it up with these options on the certificate in authorized_keys:

command="/bin/false",no-X11-forwarding,no-port-forwarding,no-agent-forwarding,permitopen="localhost:3306"

That way my clients can connect using plink.exe from putty and map their local port 3307 to port 3306 on my server like this:

plink.exe -N -L 3307:localhost:3306 user@host -i privatekey.ppk

That works great, and as far as I can see I have managed to restrict the access quite well... please correct me if I am wrong. I would love to know if there is anything else I can do to secure the server.

In order to make this simpler for me, I want to just operate with a single ubuntu login with multiple certificates, and then restrict access to data on the MySql server instead. This seems like a scenario that I can live with since I know my clients and I have only given them access to port 3306.

Now for my question:

I want to be able to easily add new certificates to this login.

The way I do it now is to create a certificate using puttygen.exe and then converting the public key using

	ssh-keygen -i -f puttykey.pub >> tmp_key 

and then adding that key with the described options to authorized_keys manually. This is just a pain in the rear, and since I am not the one who will do this once the system is in production it is completely out of the question.

So I was wondering if there is some way I could create a PHP or Bash sccript that could do this for me. Will I be allowed to do that through PHP at all? Not a big PHP wiz either, but i can work with PHP if I need to. I am used to Java. I was thinking I'd create an SSH tunnel where I could access the PHP page, which would basically allow me to upload a public key, that would then be converted and added to the authorized_keys file.

Does anyone have any input on where I should start. As I said, I have not worked with any of this technology, so don't assume that I know anything ;-)

If it is easier to maintain the file /etc/ssh/authorized_keys, then I can do that, but I haven't looked into that.

Thanks in advance,
JP

---

### Post by jpdk on 2008-09-17
Hey guys,

is there somewhere I can read about scripting to automate text file manipulation. 

A newbee in the field, so if anyone could help by pointing me in the right direction, then I'd be happy.

Thanks,
JP

---

### Post by koenn on 2008-09-17
If you're looking for serious text manipulation, you should have a look at this [http://www.faqs.org/docs/abs/HTML/string-manipulation.html](http://www.faqs.org/docs/abs/HTML/string-manipulation.html),
or get some inspiration here : [http://users.telenet.be/mydotcom/program/shell/textprocess.htm](http://users.telenet.be/mydotcom/program/shell/textprocess.htm)

If this is related to your problem of editing the keys file for passwordless ssh, 
you might find this worth a look : [http://users.telenet.be/mydotcom/howto/linux/sshpasswordless.htm](http://users.telenet.be/mydotcom/howto/linux/sshpasswordless.htm)
There's an "upload the key and add it to the file" routine in there that's almost a script.

As for adding those specifications/limitations when adding a key, consider something like this:

```

me@nix:~$ echo "ABC \"DEF\"  $(cat file1)"
ABC "DEF"  12345678945468464316464654

```
imagine that file1 contains the key (12345...) and  ABC "DEF" is free text, eg the statement you want to prepend to the key (note how to include quotes within a quoted string, using \ )

same thing, but appending to a file instead of displaying on screen 
```
echo "ABC \"DEF\"  $(cat file1)" >> authorized_keys
```

have fun.

---

### Post by jpdk on 2008-09-18
Hi Koenn,

Thanks for the link. I will definitely look into that!

/jp

---

### Post by jpdk on 2008-09-18
Hi Koenn,

This worked! Thanks a lot! I will try to package this in a neat little script and post a working solution to this, so people can do this also if they want to.

/jp

---

### Post by Dedoimedo on 2008-09-18
Hello,

1. Another few things:

You can write a script that takes certain values as input parameters and writes them to a file.

For example, a sample script:

```

#!/bin/bash

cat $1 >> file

exit 0

```

When you invoke the script with ./my-script some-text, it will write some-text to the end of the file (i.e. append it).

You can build a more complicated script using your parameters, even read them from a file...


2. There could be a problem with the generation of keys - low entropy etc, the way it happened with Debian openSSL packages just some time ago ...

Therefore, make sure you are using /dev/random for creation of keys or even manually invoke the /dev/random device.


Hope this helps ...

Dedoimedo

---

### Post by jpdk on 2008-09-18
I have just run into one problem. I have a script that uploads the key and converts it.

But when I try to append it it goes wrong.

I pass an argument into the shell script, which is the name of the putty generated key file. I convert that into a new file with the ".tmp" extension, and then I want to use $cat($1.tmp).

But that just appends the file name, not the contents. If I hardcode a filename, then it works.

ssh-keygen -i -f $1 >> $1.tmp
echo "command=\"/bin/false\",no-X11-forwarding,no-port-forwarding,no-agent-forwarding,permitopen=\"localhost:3306\" $cat($1.tmp) $1" >> authorized_keys

Thanks,
JP

---

### Post by Dedoimedo on 2008-09-18
Hello,
Why not create a file with the .tmp extension beforehand and than pass that one as input argument? Keep it simple.
Dedoimedo

---

### Post by koenn on 2008-09-18
> **jpdk said:**
>  ... and then I want to use $cat($1.tmp).


that should be ```
$( cat 1.tmp )
```
assuming 1.tmp is a filename. 
mind the ()

what you actually do is display the content of a file with ** cat filename**, 
and capture it it inside $( )  so you can include the result in another statement, like ** echo .... $( cat ... ) **

---

### Post by jpdk on 2008-09-19
This was a question of parentheses

```

ssh-keygen -i -f $1 >> $1.tmp
echo "command=\"/bin/false\",no-X11-forwarding,no-port-forwarding,no-agent-forwarding,permitopen=\"localhost:3306\" $(cat $1.tmp) $1" >> authorized_keys

```

Thanks guys!

---

