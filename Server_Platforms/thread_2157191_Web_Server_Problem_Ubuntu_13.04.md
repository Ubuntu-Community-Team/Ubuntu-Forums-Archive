---
title: "Web Server Problem Ubuntu 13.04"
date: 2013-06-24
forum: Server Platforms
---

### Post by bhennessee on 2013-06-24
I recently built a web server that i am strictly using to manage my website for my business. I am running the Ubuntu 13.04 desktop. The website will display everything properly, however I am using some javascript code to run a scrolling banner on the top and bottom of the page and it will not scroll when typing in the website name. If i use the IP address, it will scroll as it is suppose to. Since it will function properly using the IP, i know that there is no problem with my actual code. Ive changed a few things in the apache2 config file that others have suggested, but nothing i am trying will work. Any helpful advice to get this to function properly would be great! Thanks in advance!

---

### Post by trevorhanning on 2013-06-24
Could you provide some more details?  I'd like to help, but it's hard telling what needs done without detailed descriptions of a problem...

---

### Post by bhennessee on 2013-06-24
What other details would you like? Honestly, I'm a little lost with what i can do reach some type of solution to this problem. Just doesnt make sense to me as to why my website banner will scroll properly when I type in the IP address into the URL, but when I actually use the website name, it doesnt work? It obviously has to be some sort of configuration problem with the server, but I don't have a clue where at though. I've setup everything in the Apache2 configuration file properly, but for some reason it's like the server isnt recognizing my javascript code.

---

### Post by koenn on 2013-06-24
> **bhennessee said:**
>  but for some reason it's like the server isnt recognizing my javascript code.

that sort of code runs client-side, in the browser, doesn't it ?  I doubt server config has anything to do with it, unless your script does requests that the server can't interpret correctly (ip address vs hostname suggests issues with server name,  so maybe DNS, maybe virtualhost config, maybe issues with paths to or URLs for  the banner images , ...)  and your script doesn't handle that and exits. 

> **bhennessee said:**
> What other details would you like?.
the script in question + some context about the general config of the web server (like, are you using vhost,  ... ). Can you reach the banner by it's url (ie not from the scipt), ...

---

### Post by SeijiSensei on 2013-06-25
Personally, few things would make me leave a website faster than scrolling banners.

---

