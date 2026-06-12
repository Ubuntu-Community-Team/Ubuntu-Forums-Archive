---
title: "Lightweight, simple, games?"
date: 2008-11-09
forum: The Cafe
---

### Post by chris4585 on 2008-11-09
So I'm curious... what kind of games fit the title?  Linux only and preferred to be gtk.

---

### Post by cardinals_fan on 2008-11-09
* Sudoku Savant
* Gweled (a bit heavy, but fun)
* Crimson Fields
* Atomic Tanks
* GnuGo + Quarry
* Enigma (quite heavy, but I love it)
* N_v14

---

### Post by chris4585 on 2008-11-09
> **cardinals_fan said:**
> * Sudoku Savant
* Gweled (a bit heavy, but fun)
* Crimson Fields
* Atomic Tanks
* GnuGo + Quarry
* Enigma (quite heavy, but I love it)
* N_v14

atanks and enigma were pretty cool, for some reason gweled was in another language and froze up on me.

---

### Post by cardinals_fan on 2008-11-09
For n_v14, try [this]("http://www.ziva-vatra.com/index.php?aid=24&id=U29mdHdhcmU=").

---

### Post by mali2297 on 2008-11-09
[Simon Tatham's Portable Puzzle Collection](http://www.chiark.greenend.org.uk/~sgtatham/puzzles/) (sgt-puzzles in the repositories)

---

### Post by cardinals_fan on 2008-11-09
> **mali2297 said:**
> [Simon Tatham's Portable Puzzle Collection](http://www.chiark.greenend.org.uk/~sgtatham/puzzles/) (sgt-puzzles in the repositories)
**THANK YOU!**  I love dominosa already...

It's "puzzles" in the Arch repos.

---

### Post by Dr Small on 2008-11-09
> **cardinals_fan said:**
> **THANK YOU!**  I love dominosa already...

It's "puzzles" in the Arch repos.
It won't install for me :(
```
(1/1) checking for file conflicts                   [#####################] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
puzzles: /usr/bin/net exists in filesystem
Errors occurred, no packages were upgraded.

```

---

### Post by cardinals_fan on 2008-11-09
> **Dr Small said:**
> It won't install for me :(
```
(1/1) checking for file conflicts                   [#####################] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
puzzles: /usr/bin/net exists in filesystem
Errors occurred, no packages were upgraded.

```
Try this (no guarantees, warranties, or liabilities :P):
```

mv /usr/bin/net /root/
pacman -S puzzles
mv /root/net /usr/bin/
```
You'll miss the net game, but that's OK (it's not very good).

---

### Post by Dr Small on 2008-11-09
> **cardinals_fan said:**
> Try this (no guarantees, warranties, or liabilities :P):
```

mv /usr/bin/net /root/
pacman -S puzzles
mv /root/net /usr/bin/
```
You'll miss the net game, but that's OK (it's not very good).
That worked. I read up on net, and it looks to be something with Samba (may be inportant, may not be) so I'm just leaving it out for now, since I don't use Samba that often. :)

---

### Post by cardinals_fan on 2008-11-09
> **Dr Small said:**
> That worked. I read up on net, and it looks to be something with Samba (may be inportant, may not be) so I'm just leaving it out for now, since I don't use Samba that often. :)
That's what I did too.  Samba-net can stay in /root, and game-net can go in /usr/bin.

---

### Post by elmer_42 on 2008-11-09
I read the first few posts of this topic... and then I went and played atanks for 20 minutes. I should uninstall it, but it's such a fun game!

---

### Post by spupy on 2008-11-09
There is one more game I would recommend. It is a flash game, I normally despise those because they eat so much time. But this one I liked:
[http://fantasticcontraption.com/](http://fantasticcontraption.com/)

---

### Post by cardinals_fan on 2008-11-09
By the way, Shredder Chess has a pretty good version for free online.  It's not terribly hard, but is quite fun nonetheless.

[http://www.shredderchess.com/play-chess-online.html](http://www.shredderchess.com/play-chess-online.html)

---

### Post by chris4585 on 2008-11-11
One of my all time favorites.. liquidwars it may look ugly but it is awesome IMO

---

### Post by cardinals_fan on 2008-11-15
Some great CLI games:

[greed]("http://www.catb.org/~esr/greed/")
moon-buggy
asciijump

---

### Post by eternalnewbee on 2008-11-15
same Gnome
Mahjongg

---

### Post by cardinals_fan on 2008-11-15
> **eternalnewbee said:**
> same Gnome
Mahjongg
The Mahjongg game included in the gnome-games suite is quite good, but I wouldn't call it lightweight.  All the gnome-games require a bunch of GNOME dependencies.

---

### Post by Grant A. on 2008-11-15
I made a very small, extremely lightweight game in python. It's command-line based and you have to use the python shell to run it. Cheers.

```

import random

unknown = int(random.randrange(10))

welcome = raw_input("Welcome to the psychic role playing game. To continue type 'go', to read the license of this game type 'info', and to quit type 'leave': ")

if welcome == "leave":
    raw_input("\nPress enter to quit")

elif welcome == "info":
    print \
          """
\n\nThis game is licensed under the BSD License.

\n\nCopyright (c) 2008, Grant Alexander
\nAll rights reserved.

\n\nRedistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    \t\n\n* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
    \t\n\n* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
    \t\n\n* Neither the name of the copyright holder nor the names of the code's contributors may be used to endorse or promote products derived from this software without specific prior written permission.

\n\nTHIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS 'AS IS'
\nAND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
\nIMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
\nARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
\nLIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY,
\nOR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT
\nOF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
\nOR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY
\n, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
\nOTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
\nADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

          """
    raw_input("Press enter to quit")

elif welcome == "go":
    name = raw_input("Please enter your name: ")
    raw_input("\n\nTired, you walk into a psychic's room. You do not know why you are here, but you come anyways. You feel as if... something called you here.")
    raw_input("\n[Psychic] Hello son, I have called you here to bestow my powers unto you. However, I will only give you my powers if you pass this test. Do you want to go on?")

    reply1 = raw_input("\nDo you wish to continue? (y or n?): ")

    if reply1 == "y":
        raw_input("\n[" + name +"] Yes, I accept your challenge. For I am the greatest warrior in all the land, you cannot devise a test that is greater than my skills.")
        raw_input("\n[Psychic] You are an arrogant one, child. This is not a test of might or endurance, this is a test of your knowledge of the psychic abilities. You must pick a number 1 through 10 from the top of your head. If you so guess my number, then you shall inherit my powers.")

        reply2 = int(raw_input("\nChoose a number 1 - 10: "))

        
        if reply2 == unknown:
            print "\n["+ name +"] I choose the number ", reply2
            raw_input("\nPress enter to continue")
            raw_input("\n[Psychic] Yes, child! That is correct! You do infact have the psychic abilities as I suspected. I will now bestow my powers unto you.")
            raw_input("\nYou feel yourself getting lighter, you faint, and you have a dream. In your dream you see a mass of purple surrounding you. You try to fight it, but it eventually makes its way into you. You wake up, noticing the psychic is gone, and you feel at one with the universe.")
            raw_input("Press enter to quit")

        elif reply2 < unknown:
            print "\n["+ name +"] I choose the number ", reply2
            raw_input("\nPress enter to continue")
            raw_input("\n[Psychic] I am sorry, child. You do not have the abilities I sensed. Perhaps my skills aren't want they used to be. Please depart.")
            raw_input("\nWith your head hung low, you leave the room. Never to return again.")
            raw_input("\nPress enter to quit")
            

    
        elif reply2 > unknown:
            print "\n["+ name +"] I choose the number ", reply2
            raw_input("\nPress enter to continue")
            raw_input("\n[Psychic] I am sorry, child. You do not have the abilities I sensed. Perhaps my skills aren't want they used to be. Please depart.")
            raw_input("\nWith your head hung low, you leave the room. Never to return again.")
            raw_input("\nPress enter to quit")

    elif reply1 == "n":
        raw_input("\n["+ name +"] Sorry, I choose not to take your challenge.")
        raw_input("\n[Psychic] Ok, child. Please leave my hut.")
        raw_input("\nYou leave the hut wondering what the hell she was blabbering on about.")
        raw_input("\nPress enter to quit")
else:
    print "\nERROR"
    raw_input("\nPress enter to quit")

```

---

### Post by cardinals_fan on 2008-11-15
> **Grant A. said:**
> I made a very small, extremely lightweight game in python. It's command-line based and you have to use the python shell to run it. Cheers.

Epic.

---

### Post by Grant A. on 2008-11-15
> **cardinals_fan said:**
> Epic.

Yep, the license takes up half of the source code. :lolflag:

---

### Post by smartboyathome on 2008-11-15
I like to play Shogi Variants (Japanese Chess), but its a windows game. It runs great in Wine and Crossover Office though! :D

Theres Xshogi in the repos, but I don't think it is as good as Shogi Variants.

---

### Post by cardinals_fan on 2008-11-15
> **Grant A. said:**
> Yep, the license takes up half of the source code. :lolflag:
The awesome lines make it great :)
> **smartboyathome said:**
> I like to play Shogi Variants (Japanese Chess), but its a windows game. It runs great in Wine and Crossover Office though! :D

Theres Xshogi in the repos, but I don't think it is as good as Shogi Variants.
The graphics are awful, but I think gnushogi (the xshogi engine) is pretty good.

I'm becoming truly addicted to greed (mentioned on page 2).  What a great little game!

---

### Post by Eisenwinter on 2008-11-16
Try out SuperTux, you can get it from the repositories.

---

### Post by 3rdalbum on 2008-11-16
Alex the Alligator is a good platformer that reminds me of the days of using a Gameboy emulator to play Donkey Kong Land :-)  It's pretty lightweight, but for some reason it tends to block backgrounded programs from updating their interfaces. Oh well, it's fun anyway!

Another one I play is Which Way Is Up.

---

### Post by blithen on 2008-11-16
> **Grant A. said:**
> I made a very small, extremely lightweight game in python. It's command-line based and you have to use the python shell to run it. Cheers.

```

import random

unknown = int(random.randrange(10))

welcome = raw_input("Welcome to the psychic role playing game. To continue type 'go', to read the license of this game type 'info', and to quit type 'leave': ")

if welcome == "leave":
    raw_input("\nPress enter to quit")

elif welcome == "info":
    print \
          """
\n\nThis game is licensed under the BSD License.

\n\nCopyright (c) 2008, Grant Alexander
\nAll rights reserved.

\n\nRedistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

    \t\n\n* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
    \t\n\n* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
    \t\n\n* Neither the name of the copyright holder nor the names of the code's contributors may be used to endorse or promote products derived from this software without specific prior written permission.

\n\nTHIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS 'AS IS'
\nAND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
\nIMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
\nARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
\nLIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY,
\nOR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT
\nOF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
\nOR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY
\n, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
\nOTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
\nADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

          """
    raw_input("Press enter to quit")

elif welcome == "go":
    name = raw_input("Please enter your name: ")
    raw_input("\n\nTired, you walk into a psychic's room. You do not know why you are here, but you come anyways. You feel as if... something called you here.")
    raw_input("\n[Psychic] Hello son, I have called you here to bestow my powers unto you. However, I will only give you my powers if you pass this test. Do you want to go on?")

    reply1 = raw_input("\nDo you wish to continue? (y or n?): ")

    if reply1 == "y":
        raw_input("\n[" + name +"] Yes, I accept your challenge. For I am the greatest warrior in all the land, you cannot devise a test that is greater than my skills.")
        raw_input("\n[Psychic] You are an arrogant one, child. This is not a test of might or endurance, this is a test of your knowledge of the psychic abilities. You must pick a number 1 through 10 from the top of your head. If you so guess my number, then you shall inherit my powers.")

        reply2 = int(raw_input("\nChoose a number 1 - 10: "))

        
        if reply2 == unknown:
            print "\n["+ name +"] I choose the number ", reply2
            raw_input("\nPress enter to continue")
            raw_input("\n[Psychic] Yes, child! That is correct! You do infact have the psychic abilities as I suspected. I will now bestow my powers unto you.")
            raw_input("\nYou feel yourself getting lighter, you faint, and you have a dream. In your dream you see a mass of purple surrounding you. You try to fight it, but it eventually makes its way into you. You wake up, noticing the psychic is gone, and you feel at one with the universe.")
            raw_input("Press enter to quit")

        elif reply2 < unknown:
            print "\n["+ name +"] I choose the number ", reply2
            raw_input("\nPress enter to continue")
            raw_input("\n[Psychic] I am sorry, child. You do not have the abilities I sensed. Perhaps my skills aren't want they used to be. Please depart.")
            raw_input("\nWith your head hung low, you leave the room. Never to return again.")
            raw_input("\nPress enter to quit")
            

    
        elif reply2 > unknown:
            print "\n["+ name +"] I choose the number ", reply2
            raw_input("\nPress enter to continue")
            raw_input("\n[Psychic] I am sorry, child. You do not have the abilities I sensed. Perhaps my skills aren't want they used to be. Please depart.")
            raw_input("\nWith your head hung low, you leave the room. Never to return again.")
            raw_input("\nPress enter to quit")

    elif reply1 == "n":
        raw_input("\n["+ name +"] Sorry, I choose not to take your challenge.")
        raw_input("\n[Psychic] Ok, child. Please leave my hut.")
        raw_input("\nYou leave the hut wondering what the hell she was blabbering on about.")
        raw_input("\nPress enter to quit")
else:
    print "\nERROR"
    raw_input("\nPress enter to quit")

```

That is AWESOME.

---

### Post by treesurf on 2008-11-16
> **spupy said:**
> There is one more game I would recommend. It is a flash game, I normally despise those because they eat so much time. But this one I liked:
[http://fantasticcontraption.com/](http://fantasticcontraption.com/)

This is cool!

---

### Post by lukjad on 2008-11-16
What? No one mentioned Nethack? SHAME! :p

---

### Post by spupy on 2008-11-16
> **lukjad007 said:**
> What? No one mentioned Nethack? SHAME! :p

I would have mentioned it, but it doesn't fit the definition of 'simple'. :)


BTW: [http://www.thewayoftheninja.org/](http://www.thewayoftheninja.org/)
Has a linux version. ~500 levels :twisted:

---

### Post by lukjad on 2008-11-16
> **spupy said:**
> I would have mentioned it, but it doesn't fit the definition of 'simple'. :)


BTW: [http://www.thewayoftheninja.org/](http://www.thewayoftheninja.org/)
Has a linux version. ~500 levels :twisted:
Well, qt nethack is simple, as are a gew other GUI fronts for it.

---

### Post by chucky chuckaluck on 2008-11-16
there's always **bs** (battleship) and **bsdgames**.

---

### Post by init1 on 2008-11-16
[Dungeon crawl!](apt:crawl)

---

### Post by lukjad on 2008-11-16
> **init1 said:**
> [Dungeon crawl!](apt:crawl)
init1, this is not a web link.

---

### Post by init1 on 2008-11-16
> **lukjad007 said:**
> init1, this is not a web link.
No, it's an apt link. If you're using Ubuntu, it will ask you if you want to install it when you click on it.

---

### Post by lukjad on 2008-11-16
No, it doesn't.

---

### Post by chris4585 on 2008-11-16
> **lukjad007 said:**
> No, it doesn't.

Install apturl and you will see, it does work and it works well,  I've been confused though a lot of people say its in hardy by default?  or thats what I've heard, I had to install it, maybe it was a dependency of something I removed who knows

---

### Post by lukjad on 2008-11-16
Ah, thanks. :D

EDIT: Same problem.

---

### Post by cardinals_fan on 2008-11-16
> **spupy said:**
> 
BTW: [http://www.thewayoftheninja.org/](http://www.thewayoftheninja.org/)
Has a linux version. ~500 levels :twisted:
I recommended N on the first page.  You should definitely download it from the link I posted (a version using Flash 9), because the regular one lags horribly on Linux.

---

