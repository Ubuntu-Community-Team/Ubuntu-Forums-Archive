---
title: "Another Counter-Strike 1.6 problem (lol)"
date: 2009-12-20
forum: Wine
---

### Post by lunaticc on 2009-12-20
Hi,

i've been using ubuntu x64 for almost a week and it's great BUT now i wanna play Counter-Strike 1.6. I've installed wine then Steam and Counter-Strike but when i run the game and select the open find Servers or options or new game the game crashs. What can it be?

I'm using wine: 1.1.31
Ubuntu: 9.10

I've a ATi 4850

Thanks in advance

EDIT: i've updated my drivers. when i try to test 3D appears this:

> pedro@pedro-desktop:~$ atiode -P60 -H localhost:0; echo $?
2


Scroll up to aticonfig and it says this:

    >  ***note***
             atiode is a stress application you start with a required
             parameter -P which specifies the test duration and the optional
             -H parameter to target a specific display to use.  For example
             atiode -P 600 -H localhost:0 would test display 0 for 10 minutes
             the return code from the application is the test result
             0: Test successfully completed.
             1: Invalid command-line parameters.
             [COLOR=Red]2: Test failed because of rendering errors.[/COLOR]
             3: Target adapter not found.
             4: Test aborted due to unknown reason


But what kinnda errors? how can i fix it? lol

Thanks

---

### Post by lunaticc on 2009-12-20
well with so many answers i can't see the problem:P

now seriously i just found the solution. Just need to add -software to the 'shorcut' on steam. 
But i don't like playing in software mode. Someone knows how to put in openGL without crashing? :D

thanks

---

