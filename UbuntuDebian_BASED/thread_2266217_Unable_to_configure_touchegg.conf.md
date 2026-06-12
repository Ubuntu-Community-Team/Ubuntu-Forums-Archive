---
title: "Unable to configure touchegg.conf"
date: 2015-02-20
forum: Ubuntu/Debian BASED
---

### Post by Sagar_Patil on 2015-02-20
Hi, I am currently using elementary OS Luna which is based on Ubuntu 12.04. I am trying to install toughegg using this method [http://louisduhamel.fr/multitouch-os-x-like-gestures-in-elementary-os/](http://louisduhamel.fr/multitouch-os-x-like-gestures-in-elementary-os/) but it is not working. 

Here is the problem I am having

[https://www.youtube.com/watch?v=ke7PrY-5rTI&feature=youtu.be](https://www.youtube.com/watch?v=ke7PrY-5rTI&feature=youtu.be)

I have restarted my computer multiple times but no luck.

---

### Post by deadflowr on 2015-02-21
Thread Moved to Ubuntu/Debian BASED sub-forum.

---

### Post by yetimon_64 on 2015-02-21
> ```
~/.config/touchegg/touchegg.conf
```

Please note  "~" in the instructions means in your home folder. So the location to save touchegg.conf is in /home/<your-username>/.config/touchegg. In the video you link to you are trying to save to the config folder in the Downloads folder. You are saving the file to the wrong location. 

Try opening your home folder, _*then press the keyboard combination "CTRL + h" to show hidden folders and files*_, open ".config" there (the "." before the name shows it is a hidden folder) then open the folder touchegg inside .config, this is where you are supposed to copy that file to. Good luck.

---

### Post by Sagar_Patil on 2015-02-21
> **yetimon_64 said:**
> Please note  "~" in the instructions means in your home folder. So the location to save touchegg.conf is in /home/<your-username>/.config/touchegg. In the video you link to you are trying to save to the config folder in the Downloads folder. You are saving the file to the wrong location. 

Try opening your home folder, _*then press the keyboard combination "CTRL + h" to show hidden folders and files*_, open ".config" there (the "." before the name shows it is a hidden folder) then open the folder touchegg inside .config, this is where you are supposed to copy that file to. Good luck.

Yea I just found out that. I copied the .config file to [COLOR=#000000][FONT=Ubuntu Mono]~/.config/touchegg/touchegg.conf[/FONT][/COLOR] but no luck. 

Here is the video. 

[https://www.youtube.com/watch?v=r6cVbcx6Qqw&feature=youtu.be](https://www.youtube.com/watch?v=r6cVbcx6Qqw&feature=youtu.be)

---

### Post by yetimon_64 on 2015-02-21
> **Sagar_Patil said:**
> Yea I just found out that. I copied the .config file to [COLOR=#000000][FONT=Ubuntu Mono]~/.config/touchegg/touchegg.conf[/FONT][/COLOR] but no luck. 

Here is the video. 

[https://www.youtube.com/watch?v=r6cVbcx6Qqw&feature=youtu.be](https://www.youtube.com/watch?v=r6cVbcx6Qqw&feature=youtu.be) I am seeing on both occasions you change the config file you shut the window down with the close window button, but I did not see you save the file first. I suspect your method of closing the window may not be saving changes.

Try again with the "save file" button before using the window close button, I suspect it may be the one in the top right with the blue arrow on it. I don't use "scratch" so am not entirely sure of its usage or button layout. Once again, good luck.

---

### Post by Sagar_Patil on 2015-02-21
> **yetimon_64 said:**
> I am seeing on both occasions you change the config file you shut the window down with the close window button, but I did not see you save the file first. I suspect your method of closing the window may not be saving changes.

Try again with the "save file" button before using the window close button, I suspect it may be the one in the top right with the blue arrow on it. I don't use "scratch" so am not entirely sure of its usage or button layout. Once again, good luck.

I used libre and text editor. But No luck (I clicked save Ctrl + S). Now whenever ever I type touchegg in the terminal I get this 

```
Reading config from  "/home/sagar/.config/touchegg/touchegg.conf" Try to make a multitouch gesture. If everything goes well the information about the gesture must appear 
[+] Avaliable gesture: 
	 Name ->  Flick 
[+] Avaliable gesture: 
	 Name ->  Drag 
[+] Avaliable gesture: 
	 Name ->  Pinch 
[+] Avaliable gesture: 
	 Name ->  Rotate 
[+] Avaliable gesture: 
	 Name ->  Tap 
[+] Avaliable gesture: 
	 Name ->  Touch 



```

I tired to fix by using this method [https://code.google.com/p/touchegg/issues/detail?id=174](https://code.google.com/p/touchegg/issues/detail?id=174)
but no luck.  

Do I need to install the synaptiks app installed? Cause I don't have it installed.

---

### Post by yetimon_64 on 2015-02-21
You will need to await further help with this. Someone with experience with your set up needs would be better to help with this than myself past this point. Regards, yeti.

---

### Post by Vivin_Neelankavil_ on 2015-05-09
Hi @SagarPatil where you finally able to configure touchegg in elementary Os, if so can you guide me on what you did?

---

