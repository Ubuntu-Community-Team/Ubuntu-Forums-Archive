---
title: "installing printer driver, asking for root password"
date: 2011-10-05
forum: Security
---

### Post by bill23 on 2011-10-05
I am trying to install the printer driver for a LexMark printer. I get to one spot where it asks me for the administrative password. I gave it my normal password. It tells me its not right and try again. I even went to Systems >Administration > Users and Groups. There I changed my set up so I was an administrator. I tried to install the drivers but i hit the same wall ikt did not accept the password. I restarted didn't change results. Even changed the password, still a no go. Can anyone tell me what I can do to set up a root password, so I can have it on those few occasions when I might have need of it? It is important i get the printer working as I have some important documents to print.

bill23

---

### Post by OpSecShellshock on 2011-10-05
I ran into something similar, also when installing Lexmark drivers. I don't recommend this as a thing to do often, but here's what I did: rather than just running the script under my regular permissions and trying to elevate at the prompt (which as you've seen, doesn't work), I ran the entire installation script with sudo from the beginning and so elevated privileges prior to running it in the first place. That worked.

---

### Post by Johnb0y on 2011-10-05
> **OpSecShellshock said:**
> I ran into something similar, also when installing Lexmark drivers. I don't recommend this as a thing to do often, but here's what I did: rather than just running the script under my regular permissions and trying to elevate at the prompt (which as you've seen, doesn't work), I ran the entire installation script with sudo from the beginning and so elevated privileges prior to running it in the first place. That worked.

+1 - did this before, basically was admin when i installed everything...

i never user root and have another admin account to save me any possible "hick ups" that might come along...lol!

---

### Post by meatytaco on 2011-10-05
I believe this is what you are looking for. You can set up a root password by opening a terminal and typing:
```
sudo passwd
```
and enter your new password for root.

---

### Post by Johnb0y on 2011-10-05
if you were to reset it you could also try:

f you have a single-boot (Ubuntu is the only operating system on  your computer), to get the boot menu to show, you have to hold down the *Shift* key during bootup. 

 [[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb01.png[/IMG]]("http://www.psychocats.net/ubuntu/images/resetpasswordlucid01.png") 

From the boot menu, select *recovery mode*, which is usually the  second boot option.


 [[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb02.png[/IMG]]("http://www.psychocats.net/ubuntu/images/resetpasswordlucid02.png") 

After you select recovery mode and wait for all the boot-up processes  to finish, you'll be presented with a few options. In this case, you  want the *Drop to root shell prompt* option so press the Down  arrow to get to that option, and then press Enter to select it.


The  root account is the ultimate administrator and  can do anything to the Ubuntu installation (including erase it), so  please be careful with what commands you enter in the root terminal. 



 Once you're at the root shell prompt, if you have forgotten your  username as well, type 
ls /home
 That's a lowercase *L*, by the  way, not a capital *i*, in *ls*. You should then see a list  of the users on your Ubuntu installation. In this case, I'm going to  reset Susan Brownmiller's password.

 To reset the password, type 
passwd  [I]username

[/I]
 where *username* is the username you want  to reset. In this case, I want to reset Susan's password, so I type  passwd susan


  You'll then be prompted for a new password. When you type the  password you will get [no visual response  acknowledging your typing]("http://www.psychocats.net/ubuntu/passwordinterminal"). Your password is still being accepted.  Just type the password and hit *Enter* when you're done. You'll  be prompted to retype the password. Do so and hit *Enter* again. 



 Now the password should be reset. Type 
exit


 to return to the recovery menu.  [[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucidthumb03.png[/IMG]]("http://www.psychocats.net/ubuntu/images/resetpasswordlucid03.png")   
After you get back to the recovery menu, select *resume normal  boot*, and use Ubuntu as you normally would—only this  time, you actually know the password! 

Source:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by bill23 on 2011-10-05
Thanks for the suggestions and I will try it. 

Meatytaco, I typed in; sudo psswd then what I wanted for the root privilege password, it was not accepted.

Going to follow your (JohnB0y) suggestions. If they work I'll be back with a good post?

bill23

---

### Post by Johnb0y on 2011-10-05
shame but i hope that something works for you soon! nothing worst than having a little "prickly" issue like that holding you up! lol

---

### Post by meatytaco on 2011-10-05
That's strange :/ I've done that twice on mine now... Sorry

---

### Post by meatytaco on 2011-10-05
Just making sure, did you enter your -sudo- password before you entered what you wanted for your -su- password? If not, that would muddy things up. O.o

Should look like this
```
lobos@Taquito:~$ sudo passwd
[sudo] password for lobos: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
lobos@Taquito:~$ 



```

---

### Post by bill23 on 2011-10-05
I did forgot to put 'sudo' before and it did screw it up. said psswd not a command. I'll go back to try again.

---

### Post by meatytaco on 2011-10-05
lol yeah.. do make sure you get the "a" in passwd.

---

### Post by bill23 on 2011-10-05
I have a new motto "If at first you don't succeed, fail fail again" 
I entered sudo psswd and I got what is below which was repeated another two times.

[sudo: psswd: command not found
root@bill48-desktop:~# [  83.32518] Inbound IN= eth0 OUT=MAC=00:e0:b8:6e:c6:df:00:1e:be:ff:1b:db:08:00 SRC=58.218.199.227 DST=72.222.241.101 LEN=40 TOS=0x00 TTL=115 ID=256 DF PRO TO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN=URGP=0]

I am going back and  try:
[sudo chng psswd] in the command line? What do you think?

---

### Post by meatytaco on 2011-10-05
the command is "passwd" not the "psswd" you keep typing.  Make sure to use "sudo p**a**sswd" when trying to change the root password. O.o

---

### Post by bill23 on 2011-10-05
Success!!! 

I go through all that trouble only to find the software I was trying to install is not supported by my system. Bummer! :(

I want to thank you all for your help and a single letter can make a difference.

bill23

---

### Post by meatytaco on 2011-10-05
Aww :( sorry to hear that. Ya. One letter does :P

---

### Post by bill23 on 2011-10-05
I was considering download the software and using 'Wine' to set it up, then thought that may not be a smart move? I certainly do not want to make matters worse then they already are. My alternate printer a Canon Pixma series which is also not supported with Linux.

What is with these companies not offering support to tens of thousands of Linux users and their printers. They are losing money and the stronger and larger Linux grows the more money they will lose.

It looks like I am going to have to do some shopping for a printer compatible with Linux?

bill23

---

### Post by meatytaco on 2011-10-05
Got me on that one, i haven't messed with printing and linux... Hopefully someone else will have input.

---

### Post by OpSecShellshock on 2011-10-05
Seems odd to me. I have a Lexmark 3600-4600 series, and I grabbed the Linux driver from their site and it worked fine. I wonder if it's a 32/64 bit support issue?

---

### Post by bill23 on 2011-10-06
I think the newer ones may have drivers set for Linux, the ones I had were old in the neighborhood of ten years. So I should not have been too surprised when they were not supported. I just assumed they would work regardless of what type of Operating System you were using? 
I'll check  out the LexMark 3600-4600 series, maybe there is one that will fit in my budget? I think there is a difference in the drivers if it is a 32 bit or a 64 bit system?

bill23

---

### Post by OpSecShellshock on 2011-10-06
> **bill23 said:**
> I think the newer ones may have drivers set for Linux, the ones I had were old in the neighborhood of ten years. So I should not have been too surprised when they were not supported. I just assumed they would work regardless of what type of Operating System you were using? 
I'll check  out the LexMark 3600-4600 series, maybe there is one that will fit in my budget? I think there is a difference in the drivers if it is a 32 bit or a 64 bit system?

bill23

Well what I've noticed is that (even now!) a lot of printer manufacturers still don't support 64-bit architecture in their printers, but there are 32-bit wrappers that can be installed in order to get around that as long as the drivers themselves exist for Linux. Frankly, I'm surprised that ink is still available for a printer that's 10 years old. Even with the newer ones you have to practically be willing to starve to death to keep the ink flowing.

---

