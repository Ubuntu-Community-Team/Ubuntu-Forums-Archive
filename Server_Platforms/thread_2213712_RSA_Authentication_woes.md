---
title: "RSA Authentication woes"
date: 2014-03-28
forum: Server Platforms
---

### Post by ally2 on 2014-03-28
Morning guys I am still having problems with RSA keys I have been following a few guides but have reached the stage where I am now stumped it probably is something simple. 

Below are the steps I have completed

Created the Public and Private Keys on Windows Box using Puttygen

Created a blank text file in notepad and copied the public key ensuring the key fits all on one line saved document as authorized_keys.txt

Saved Public and Private keys on Windoze box in putty folder just called them ubuntupri and ubuntupub

Logged on server as Ally in the home/ally directory there is a hidden folder called .ssh

within this directory I used WinSCP to copy across the authorized_keys.txt file created on the windoze box

I then did a chmod 700 on the file to set the permissions

In Putty under the SSH / AUTH settings I have told Putty to use the private key on the windows box

When I attempt to connect through SSH I get a**[COLOR=#ff0000] " Server has refused Key issue"[/COLOR]**

My inital thoughts am I saving the public key in the right directory? or is there another config file I have to edit?

Many Thanks

---

### Post by steeldriver on 2014-03-28
AFAIK he public key needs to be in a file called exactly ~/.ssh/authorized_keys file on the target server - not authorized_keys**.txt** for example

The ~/.ssh/authorized_keys file *may* need to be mode 600 (-rw------)

Although I'm a big WinSCP fan, I really would recommend doing it [the way I described yesterday]("http://ubuntuforums.org/showthread.php?t=2213563") - it avoids potential issues such as Windows encodings / line endings

I'm assuming you copied the OpenSSH format of the key from puttygen NOT the native putty key format

---

### Post by ally2 on 2014-03-28
Hey thanks for the response I have been fighting with it all morning and am still getting nowhere it :)

The user I am logging into the server remotely is called Ally he is a member of the sudoers 

I when creating the key in putty gen I just literally highlight the key and copy it into a text file called authorized_keys.txt

SSH-2-RSA

ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEAhb5KZJG94Z86bINmp5FzTURB96tNR1JnK1R/99BgHohiX3wgeBklmgct/lQmlyrWrKgaLjDEMZD5glbCu1tEmtI2N2/YiHfWbkm4w/kmJUcCb1MeJtfNrQF67lmUFQ+4FfEuFu9tBRO2R6/zLO26kdp7jQE2va3nud9HmXKrqB4amHyt8DP10W8204V+f9rW+qsZ9VeJpuVDJtzJ25+r8OgT9BsfdWuEZpkih2ZwlkbE8+3ITxMSjPzCyuWDc3pjsrFCAiOMF/0S1/vEiUtmZ2ZUpko5XX9XFbowQpkZU1eguCYq9PN1DxBt+OvRYon2ke0YSQLlCjtVnWsAVgAjCQ== rsa-key-20140328

Now looking at the above do I have to omit the ssh-rsa at the start of the text, and the == rsa-key 20140328 when I copy this public key to the server I have tried different variations :)

From the server side of things ally has /home/ally a folder called .ssh exists and I have set the permissions chmod 700
and the file authorized_users has permissons set chmod 600

I have tried your method of pasting the key directly from a text file into vim avoiding WinSCP althogether

Still am getting the server has refused key issue

Do I have to configure sshd?

---

### Post by ally2 on 2014-03-28
I am going to try what you suggested with the exporting the OpenSSH format this wasn't explained in any guide I have read :) it just literally says copy the key grrrrrrrrrrr

---

### Post by steeldriver on 2014-03-28
I always just 'Select all' and 'Ctrl-c' from the "Public key for pasting into OpenSSH authorized_keys file" frame at the top of the puttygen window

[ATTACH=CONFIG]251534[/ATTACH]

Then paste into a (password based) session using right click (followed by 'Enter' and then 'Ctrl-d' to return to the shell) - you could start an editor (nano / vi etc.) and paste into that instead of using 'cat' (which is a bit oldschool)

[ATTACH=CONFIG]251536[/ATTACH]

[ATTACH=CONFIG]251535[/ATTACH]

The other pretty painless way to do it is to save the public key in putty's native format (RFC4716?), copy THAT file over with WinSCP, and then **import **it on the server side using ssh-keygen

```

$ ssh-keygen -i -f steeldriver.pub  >> ~/.ssh/authorized_keys

```

It does not appear to need the -m option to specify the key format

---

### Post by ally2 on 2014-03-28
I have attached some details of my work the RSA Key As you can when I pasted it from Putty gen to the server via VIM the text isn't appearing on one line is this a problem? 

The second photo shows permissions for the file

and the third photo shows permissions for directory

Still fighting with it :) If I do get it working will document

---

### Post by steeldriver on 2014-03-28
No that should be fine - you're just seeing the line wrapping of the displaying terminal

The authorized_keys file should probably be mode 600 (-rw-------) not 700 (-rw**x**------) - I'm not sure it matters but change it anyway

---

### Post by ally2 on 2014-03-28
Still am having no joy and have a headache :) attached are my putty settings 

To summarize my attempts to get this to work

generated key on host via use of puttygen 

highlighted and copied the key into a vim file called authorized_keys on the server located in home/ally/.ssh

directory permissions are 700 and authorized_keys file permissions are 600

Haven t edited any config files 

Going to try this [http://kb.mediatemple.net/questions/1626/Using+SSH+keys+on+your+server#all/creating-an-ssh-key-in-putty--](http://kb.mediatemple.net/questions/1626/Using+SSH+keys+on+your+server#all/creating-an-ssh-key-in-putty--)

once my headache has gone lol

---

### Post by ally2 on 2014-03-28
[http://www.server-world.info/en/note?os=Ubuntu_12.04&p=ssh&f=2](http://www.server-world.info/en/note?os=Ubuntu_12.04&p=ssh&f=2)

Followed the above guide exactly and same issue the server is refusing key 

this is driving me nuts :)

---

### Post by steeldriver on 2014-03-28
... at this point maybe you should post your /etc/ssh/sshd_config file?

---

### Post by ally2 on 2014-03-31
had another go this morning and have got it working :)

[http://www.walkernews.net/2009/03/22/how-to-fix-server-refused-our-key-error-that-caused-by-putty-generated-rsa-public-key/](http://www.walkernews.net/2009/03/22/how-to-fix-server-refused-our-key-error-that-caused-by-putty-generated-rsa-public-key/)

Added my hostname to the end of the rsa key and ensured the format was correct using above guide now works like a charm. 

Thanks for your help :)

---

### Post by ally2 on 2014-03-31
If anyone is using SSH to administrate there server from a windows box and requires instructions, Here are the notes figured it may be useful to noobs like myself.

[COLOR=#000000][FONT=Tahoma]Use Putty Gen to generate Public and Private keys,[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Save private key and public Key to putty folder[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]highlight and copy the public key[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]On the Linux machine navigate to users home directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]ls -a find the .ssh folder [/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]create a file in the .ssh folder called authorized_keys[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma] 2) Delete the first two and the last line,

3) Join the remaining lines into one single line, by using the Shift+J command shortcut. Remember to trim space between two line joined by CTRL+J command.

4) Insert ssh-rsa keyword (with one trailing space) in front of the single line.

5) [ OPTIONAL ] Append [COLOR=#FF0000]**Login_ID**[/COLOR]@[COLOR=#FF0000]**Host_name**[/COLOR] keyword (with a initial space) at the end of the single line (replace *Login_ID* and *Host_name* with your SSH login ID and host name accordingly).

[IMG]file:///C:/DOCUME~1/ADMINI~1/LOCALS~1/Temp/enhtmlclip/Image(7).jpg[/IMG][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]( Change Password Authetication)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Edit  etc/ssh/sshd_config[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]After verifying you can log into the Linux PC without using a password, password authentication will still work should RSA not work for any reason, which is a security vulnerability. Password authentication can be turned off completely by changing the following entries in the etc/ssh/sshd_config file on the Linux PC. To use RSA authentication exclusively, make the following changes to the sshd_config to force public-key authentication and disable password authentication:
[COLOR=#5898FF][B]PasswordAuthentication no
PubkeyAuthentication yes
RSAAuthentication yes[/B][/COLOR][COLOR=#5898FF]**Restart SSH**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma] restart the Linux PC SSH server using [COLOR=#5898FF]***sudo /etc/init.d/ssh restart*** [/COLOR]from a terminal on the Linux PC before logging in. [/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Load putty on windows under SSH / AUTH settings add private key on the windows box

Connect using to server through Putty 
[/FONT][/COLOR]

---

### Post by steeldriver on 2014-03-31
Hi ally2 glad you got it working

However the steps you have written above lead me to believe that you copied and modified the native PuTTY (RFC4716) key - if you had selected + copied the key directly from the main PuTTY pane (NOT saved it to file first) then manual editing of the key should not have been necessary i.e.

Example PuTTY .pub key file contents
```

---- BEGIN SSH2 PUBLIC KEY ----
Comment: "rsa-key-20140331"
AAAAB3NzaC1yc2EAAAABJQAAAIB/C72/LbiSFWpQIxlFXf19RQPX9FuVFHd1LyvC
TQCZMTi3pdzut4tbvF8J/3LwaBMNPl47V4qhLKc4xr0mRDd3mtE+4dV8ZCXUB8MZ
zQsxsyIOppgn6eydQyKLZLXjkpwo2CdUB66gEPsETJwPg69nnVmb9ai+7UgdRWZx
ZF/C0w==
---- END SSH2 PUBLIC KEY ----

```

Same key, copied right from the display area (**"Public key for pasting into OpenSSH authorized_keys file:"**)
```

ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIB/C72/LbiSFWpQIxlFXf19RQPX9FuVFHd1LyvCTQCZMTi3pdzut4tbvF8J/3LwaBMNPl47V4qhLKc4xr0mRDd3mtE+4dV8ZCXUB8MZzQsxsyIOppgn6eydQyKLZLXjkpwo2CdUB66gEPsETJwPg69nnVmb9ai+7UgdRWZxZF/C0w== rsa-key-20140331

```

Thumbnail of the PuTTY pane that I'm talking about is attached

[ATTACH=CONFIG]251609[/ATTACH]

---

### Post by ally2 on 2014-03-31
Kool thanks for the heads up :)

---

