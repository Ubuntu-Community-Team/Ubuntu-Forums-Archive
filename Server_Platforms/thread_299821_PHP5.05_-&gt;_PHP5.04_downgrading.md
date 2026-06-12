---
title: "PHP5.05 -&gt; PHP5.04 downgrading?"
date: 2006-11-14
forum: Server Platforms
---

### Post by stoiss on 2006-11-14
Hi,

I recently installed Ubuntu (Breezy) on a small (via epia VE5000) server along with "LAMP".
Everything is running smoothly sofar except that I'm getting the following error when I execute PHP code:

**"Fatal error: Only variables can be passed by reference"**

The PHP version I'm using is PHP5.05 and after some searching I find that there were some changes between version 5.04 and 5.05:

```
//fails
Foo(Bar());

//works
$bar = Bar();
Foo($bar);

```

This means I either have to rewrite a lot of code, that I didn't write myself in the first place or downgrade to PHP5.04. I would prefer the later as I'm not willing to go through a couple thousand lines of code with my minimal PHP knowledge.

I have tried to downgrade with the following command:

sudo apt-get install php5=5.04

However this isn't working as apt-get can't find that version.

Does anyone have a solution to this?

Thanks in advance!

/stoiss

---

### Post by marianom on 2006-11-14
i'm checking my php 5.16 ini file and there it says:

```

; Whether to enable the ability to force arguments to be passed by reference
; at function call time.  This method is deprecated and is likely to be
; unsupported in future versions of PHP/Zend.  The encouraged method of
; specifying which arguments should be passed by reference is in the function
; declaration.  You're encouraged to try and turn this option Off and make
; sure your scripts work properly with it in order to ensure they will work
; with future versions of the language (you will receive a warning each time
; you use this feature, and the argument will be passed by value instead of by
; reference).
allow_call_time_pass_reference = Off

```

Do you have that variable in your php.ini? Can you turn it on to check if it still works?

However I suggest you talk to the owner of the app and encourage him to buy some time and fix that in every file so that he can use future versions.

---

### Post by stoiss on 2006-11-15
```
allow_call_time_pass_reference = On
```

This is what it's set to in my php.ini, however I still get errors when executing the scripts.

I know the maintainer of the code is probably going to fix it .. eventually.

Untill then I would like to downgrade to PHP5.04 or ealier.

I understand you can force an earlier version to be installed by post fixing the install command with "=specificversion".

Does anyone know a working postfix. One that exists in the repository?

---

