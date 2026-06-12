---
title: "php only doing include"
date: 2011-09-28
forum: Server Platforms
---

### Post by orang on 2011-09-28
Okay, so after following an out-of-date LAMP with SSL walkthrough for a different linux distribution, I attempted to undo everything and just install from packages. After tons of problems from multiple php installs, I finally got it working but with a quirk.

My scripts start with 

<?php
include("/var/wwwssl/header.php");

It will show my header but nothing else, not even errors.

I've tried sudo aptitude reinstall libapache2-mod-php5 several times. I'm thinking next I will reinstall php from source and re uninstall it. If I do this will I need to. /configure it the same?

Are there any diagnoses that could help me out?

---

### Post by ktmom on 2011-09-29
I'd also suggest that you replace the code in your file with 

<?php phpinfo(); ?>

If that displays the test page, then the problem is with your code.  Is the code compatible with the installed version of PHP? Even if it worked on another server, it may not be compatible with the current PHP release you have installed.

---

### Post by business_user on 2011-09-29
If you're not getting error messages and want them you could try enabling the error reporting in you php.ini file. This has some security implications  so you might want wo temporarily enable error reporting just while you fix the bugs.

---

### Post by docbop on 2011-09-29
I would run php -l filename.php

That runs the php syntax checker so you can check outside apache.

---

### Post by orang on 2011-09-29
Well i had this script up on a different server before i set this one up. It worked over there. The only code i"ve changed is the various ways of doing "include()"

But the problem shouldnt be affected; the include() part is working. When i comment it out, the rest of the page displays exactly as it is supposed to. I have a seperate page with phpinfo() displayed in all its glory here - wikifightgame.com/testphp.php

---

### Post by Entilza on 2011-09-29
Something in the include is probably causing an error then, did you check the error log file in apache?

---

### Post by Vegan on 2011-09-29
Seems to be a spat of of PHP problems cropping up.

Windows and Linux alike. Not good.

please post the code so we can read it and figure out a fix or workaround

---

### Post by orang on 2011-09-30
Aargh. I was positive I'd done everything to check that it wasn't my scripts.

Apparently I forgot to try commenting out my included functions page. It isn't including header.php that breaks it, its including functions.php that does.


So yeah, problem is in my code, I'll find it. >_< sorry guys and thank you!

---

