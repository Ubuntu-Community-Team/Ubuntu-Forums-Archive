---
title: "Help With Tor Bundle"
date: 2011-01-12
forum: Security
---

### Post by JPKnowMad on 2011-01-12
I am trying to install and run the Tor Browser bundle from a flash drive. I have downloaded the file and extracted it to the flash drive. When I go in to run the "start tor browser" script all I get is the actual text pop up or if I select run from terminal or just run, terminal pops up for just a sec and then disappears with nothing happening. Where have I gone wrong? I am following the torproject instructions.

I am running 10.10

---

### Post by bodhi.zazen on 2011-01-12
Run the script from a terminal and post any error messages you get.

---

### Post by JPKnowMad on 2011-01-13
When I select run from terminal, the only thing that goes on is terminal pops up for a split second then disappears. If I have terminal already open or not, it does the same thing.

---

### Post by bodhi.zazen on 2011-01-13
No, not run from terminal.

Open a terminal and run the program from the command line. This way you can see the error message.

---

### Post by JPKnowMad on 2011-01-14
I am fairly ubuntu retarded, so could you help me with how to run the script in terminal. I am a newer ubuntu convert and still try to use the gui stuff for upgrades/updates/software. Thanks for any help.

---

### Post by bodhi.zazen on 2011-01-14
> **JPKnowMad said:**
> I am fairly ubuntu retarded, so could you help me with how to run the script in terminal. I am a newer ubuntu convert and still try to use the gui stuff for upgrades/updates/software. Thanks for any help.

What is the program called ? tor-browser (not sure off the top of my head).

Where did you download it to ? Desktop ? Downloads ?

What directory is it extracted to ? Desktop/torbundle ?

Assuming the above,

Open a terminal

```
cd ~/Desktop/torbundle
./tor-browser
```

cd into the directory you downloaded and extracted tor bundle into and put a "./" (witho9ut quotes) in front of the name of the browser.

to learn the terminal, or bash, see:

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by JPKnowMad on 2011-01-14
Thank you so much. I'll do some hw with that link.

---

### Post by JPKnowMad on 2011-01-14
Thank you so much. I'll see how that works, and I'll do some homework. Thanks for the link.

---

### Post by JPKnowMad on 2011-01-14
ok I tried to cd into the script like you said, but for some reason it says it doesn't exist. I tried to just cd into the media folder where the flash is and got this

jimmie@jimmie-desktop:~$ cd ~/media
bash: cd: /home/jimmie/media: No such file or directory
jimmie@jimmie-desktop:~$ 

i have tried it with the flash as well and keep getting this. I dont know if this has anything to do with it, but I have ubuntu running on a 32gb SSD and have a 500gb wd hd for daily storage.

---

### Post by JPKnowMad on 2011-01-14
I managed to get into the directory containing the start-tor-browser script without using the ~ symbol like in your example. 

jimmie@jimmie-desktop:/media/JPFlash/tor-browser_en-US$ cd /media/JPFlash/tor-browser_en-US./start-tor-browser
bash: cd: /media/JPFlash/tor-browser_en-US./start-tor-browser: No such file or directory
jimmie@jimmie-desktop:/media/JPFlash/tor-browser_en-US$ 

This is what I get when I try to run the actual script.

---

### Post by JPKnowMad on 2011-01-14
Ok I managed to get it running with terminal. I'm just slow. This popped up in terminal while vidalia was loading.

Launching Tor Browser Bundle for Linux in /media/JPFlash/tor-browser_en-US
Qt: Session management error: None of the authentication protocols specified are supported

What are the authentication protocols and what can I do to fix this?

---

### Post by JPKnowMad on 2011-01-14
Ok, So I have it running now. I didn't realize how much slower everything is with tor. Haha, now that i have it figured out, i'm thinking about getting rid of it. Would there be any advantage to running mozilla from a thumb drive as opposed to from my desktop?

I was thinking using socksify and running mozilla on a thumb drive, along with all your other security threads. I am hoping to read them soon, but it would probably be better if i did some work on that linuxcommand site first, as this project has made me realize just how little I know. How would I go about ensuring the removal of all firefox files from my computer?

---

### Post by bodhi.zazen on 2011-01-14
Google search that error message + TOR.

Try moving the entire directory to your home directory.

---

### Post by stleoric on 2011-07-04
Hello,

I just installed Tor Browser Bundle ([https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)) and I get errors while trying to run it.

```
Launching Tor Browser Bundle for Linux in /home/xyz/Programs/tor-browser_en-US
./App/vidalia: 1: : not found
./App/vidalia: 1: ELF: not found
./App/vidalia: 2: &#65533;&#65533;
                    aN: not found
./App/vidalia: 3: &#65533;&#65533;: not found
vpp/vidalia: 3: M%h&#65533;&#65533;
   .&#65533; not found
./App/vidalia: 3: ./App/vidalia: 4: &#65533;
%: not found                         l&#65533;t3&#65533;&#65533;&#65533;&#65533;: not found

./App/vidalia: 5: &#65533;
&#65533;: not found
./App/vidalia: 6: /&#65533;n&#65533;: not found
./App/vidalia: 7: &#65533;C&#65533;: not found
&#65533;&#65533;: not found8: 
./App/vidalia: 8: :&#65533;: not found
./App/vidalia: 9: &#65533;&#65533;: not found
./App/vidalia: 10: #V&#65533;6&#65533;: not found
./App/vidalia: 14: cannot open &#65533;&#65533;H&#65533;
                                    : No such file
./App/vidalia: 14: &#65533;
                    &#65533;}&#65533;&#65533;Q
x
 &#65533;
  &#65533;s&#65533;$&#65533;&#65533;
&#65533;&#65533;
    I&#65533;&#65533;
         &#65533;&#65533;
            i
              &#65533;u[
                       &#65533;}&#65533;
hK&#65533;3&#65533;
 &#65533;&#65533;=
    Zt&#65533;C&#65533;&#65533; 
                    s&#65533;&#65533;    
                                 M
                                     &#65533;*p&#65533;&#65533;: not found
./App/vidalia: 15: &#65533;: not found
./App/vidalia: 16: Syntax error: ")" unexpected

Exited cleanly. Goodbye.
```I'm pretty sure I followed the instructions correctly (download the latest tar, extract, run). Google search doesn't yield any solutions that I haven't tried (installing into different directories, running sudo).

Any help, advice or pointer would be appreciated.
Thanks.

EDIT:
FIXED - apparently, I downloaded the wrong bundle - x86_64 instead of i686.
A classic noob mistake.[URL="http://www.emoticonsworld.org/data/media/72/me_gusta.png"]
[/URL]

---

