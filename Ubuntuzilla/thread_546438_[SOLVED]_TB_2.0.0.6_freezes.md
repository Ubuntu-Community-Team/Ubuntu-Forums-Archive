---
title: "[SOLVED] TB 2.0.0.6 freezes"
date: 2007-09-08
forum: Ubuntuzilla
---

### Post by habtish on 2007-09-08
Hello,

I used ubuntuzilla to download and install TB 2.0.0.6 and can not use TB since then.

My first problem was that the launchers [application menu and gnome panel] were not updated to run "thunderbird" and were pointing to 'mozilla-thunderbird'. So i fixed this to point to thunderbird and seemed to work, but alas TB freezes after 2 minutes or so.

Running it in the terminal seemed to work. But I kept on going through different settings and menu entries to see if it would free again and when I went to "Tools>import" TB did freeze and below is the rather extensive output from my terminal: ```

$ thunderbird 
*** glibc detected *** /opt/thunderbird/thunderbird-bin: free(): invalid next size (fast): 0x09169440 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb72dc7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb72dfe30]
/usr/lib/libstdc++.so.5(_ZdlPv+0x23)[0xb7452a53]
/usr/lib/libstdc++.so.5(_ZdaPv+0x1f)[0xb7452aaf]
/opt/thunderbird/thunderbird-bin[0x82923d8]
/opt/thunderbird/thunderbird-bin[0x829cb9a]
/opt/thunderbird/libxpcom_core.so(_ZN13nsCOMPtr_base18assign_with_AddRefEP11nsISupports+0x2c)[0xb7dd92fc]
/opt/thunderbird/thunderbird-bin[0x86ddd7c]
/opt/thunderbird/thunderbird-bin[0x86e4e26]
/opt/thunderbird/thunderbird-bin[0x86dc264]
/opt/thunderbird/thunderbird-bin[0x8501e7e]
/opt/thunderbird/libxpcom_core.so(PL_HandleEvent+0x27)[0xb7e226a7]
/opt/thunderbird/libxpcom_core.so(PL_ProcessPendingEvents+0x84)[0xb7e225d4]
/opt/thunderbird/libxpcom_core.so[0xb7e2425d]
/opt/thunderbird/thunderbird-bin[0x829b1c5]
/usr/lib/libglib-2.0.so.0[0xb785240d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7828df2]
/usr/lib/libglib-2.0.so.0[0xb782bdcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb782c335]
/opt/thunderbird/thunderbird-bin[0x829b945]
/opt/thunderbird/thunderbird-bin[0x86ddb51]
/opt/thunderbird/thunderbird-bin[0x86e7ee7]
/opt/thunderbird/thunderbird-bin[0x86218d8]
/opt/thunderbird/thunderbird-bin[0x8621032]
/opt/thunderbird/thunderbird-bin[0x850533b]
/opt/thunderbird/thunderbird-bin[0x85016ac]
/opt/thunderbird/libxpcom_core.so(XPTC_InvokeByIndex+0x29)[0xb7e3cb55]
/opt/thunderbird/thunderbird-bin[0x80b40f8]
/opt/thunderbird/thunderbird-bin[0x80bb3e1]
/opt/thunderbird/libmozjs.so(js_Invoke+0x636)[0xb7ea9fa6]
/opt/thunderbird/libmozjs.so(js_Interpret+0x3ead)[0xb7eaf5bd]
/opt/thunderbird/libmozjs.so(js_Invoke+0x71d)[0xb7eaa08d]
/opt/thunderbird/libmozjs.so(js_InternalInvoke+0xc3)[0xb7eaa593]
/opt/thunderbird/libmozjs.so(JS_CallFunctionValue+0x4e)[0xb7e7df3e]
/opt/thunderbird/thunderbird-bin[0x84f5987]
/opt/thunderbird/thunderbird-bin[0x852a410]
/opt/thunderbird/thunderbird-bin[0x84697dc]
/opt/thunderbird/thunderbird-bin[0x8469ca8]
/opt/thunderbird/thunderbird-bin[0x84d0a67]
/opt/thunderbird/thunderbird-bin[0x82dff26]
/opt/thunderbird/thunderbird-bin[0x8404799]
/opt/thunderbird/thunderbird-bin[0x840149d]
/opt/thunderbird/thunderbird-bin[0x82dfb6d]
/opt/thunderbird/thunderbird-bin[0x82df283]
/opt/thunderbird/thunderbird-bin[0x84ee0d6]
/opt/thunderbird/thunderbird-bin[0x84ed23f]
/opt/thunderbird/thunderbird-bin[0x84e6f16]
/opt/thunderbird/thunderbird-bin[0x829c389]
/opt/thunderbird/thunderbird-bin[0x8294e4f]
/opt/thunderbird/thunderbird-bin[0x82994b0]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7b1a6b0]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb789d62b]
/usr/lib/libgobject-2.0.so.0[0xb78ae103]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78af3ef]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78af7e9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c2ee18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x183)[0xb7b139c3]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x317)[0xb7b14bc7]
/usr/lib/libgdk-x11-2.0.so.0[0xb799612a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7828df2]
/usr/lib/libglib-2.0.so.0[0xb782bdcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb782c179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b15044]
======= Memory map: ========
08048000-08d04000 r-xp 00000000 08:12 1795653    /opt/thunderbird/thunderbird-bin
08d04000-08d1e000 rwxp 00cbb000 08:12 1795653    /opt/thunderbird/thunderbird-bin
08d1e000-0a011000 rwxp 08d1e000 00:00 0          [heap]
af285000-af2fb000 r-xp 00000000 08:12 1128857    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
af2fb000-af378000 r-xp 00000000 08:12 1130338    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
af378000-af379000 ---p af378000 00:00 0 
af379000-afb79000 rwxp af379000 00:00 0 
afb79000-afb7a000 ---p afb79000 00:00 0 
afb7a000-b037a000 rwxp afb7a000 00:00 0 
b037a000-b037b000 ---p b037a000 00:00 0 
b037

```Not sure what I am doing wrong here, I would appreciate any suggestions...
Thanks!

---

### Post by nanotube on 2007-09-08
> **habtish said:**
> Hello,

I used ubuntuzilla to download and install TB 2.0.0.6 and can not use TB since then.

My first problem was that the launchers [application menu and gnome panel] were not updated to run "thunderbird" and were pointing to 'mozilla-thunderbird'. So i fixed this to point to thunderbird and seemed to work, but alas TB freezes after 2 minutes or so.


the links were not updated because "mozilla-thunderbird" should work - it works just fine for me. :) i am not sure if this is related to the freezing problem, though...

> 
[...]
Not sure what I am doing wrong here, I would appreciate any suggestions...
Thanks!

heh well, i don't know how to read a mozilla backtrace... i've never run into a similar problem around here. 

you could have better luck asking on the mozilla support channels... or maybe someone else here can jump in. :)

---

### Post by habtish on 2007-09-11
> **nanotube said:**
> 

heh well, i don't know how to read a mozilla backtrace... i've never run into a similar problem around here. 

you could have better luck asking on the mozilla support channels... or maybe someone else here can jump in. :)

Posted message on mozillazine forum, no replies in 3 days.. that is the defacto official Mozilla support forum right?

---

### Post by nanotube on 2007-09-12
i am not sure... 
you could also try the mozilla irc channel (see info at [http://www.mozilla.org/developer/](http://www.mozilla.org/developer/))

---

### Post by nanotube on 2007-09-12
by the way...
have you tried starting with a fresh profile, to see if it solves the crashing problem?
run ```
thunderbird -P
```
and make a new profile...
or just move your existing thunderbird profile out of the way:
```
mv ~/.thunderbird ~/.thunderbird.bak
```

if that solves the problem, you can then manually move your mail over, and reinstall your extensions...

if that doesn't help, then i don't know. :)

---

### Post by habtish on 2007-09-14
> **nanotube said:**
> by the way...
have you tried starting with a fresh profile, to see if it solves the crashing problem?


That was the second item on my list of things to try. I just ran TB in safemode ```
 /opt/thunderbird/thunderbird -safe-mode
``` and Tb didn't crash. So I do believe it was an extension or a theme causing the crash. I have removed my extensions and have left a regular TB session open. We'll see if it doesn't crash this time. [ One of the extensions had an incompatibility message and was disabled, it could have been something with this add-on that was messing TB up], but thanks for a great script that allows us to easily get the latest Mozilla releases and thanks for your follow up with my post as well!!

Cheers

---

### Post by nanotube on 2007-09-15
> **habtish said:**
> That was the second item on my list of things to try. I just ran TB in safemode ```
 /opt/thunderbird/thunderbird -safe-mode
``` and Tb didn't crash. So I do believe it was an extension or a theme causing the crash. I have removed my extensions and have left a regular TB session open. We'll see if it doesn't crash this time. [ One of the extensions had an incompatibility message and was disabled, it could have been something with this add-on that was messing TB up], but thanks for a great script that allows us to easily get the latest Mozilla releases and thanks for your follow up with my post as well!!

Cheers

and thank you for your feedback, and working with me to try to resolve the problem. :)

please let us know by posting back here once you narrow it down to a particular extension - that way other users in the future may save themselves some trouble. :)

---

### Post by Lord Illidan on 2007-10-06
I had a similar problem, and it was the Tango Icons extension for Thunderbird. It would crash even on Send/Recieve.

---

### Post by nanotube on 2007-10-06
> **Lord Illidan said:**
> I had a similar problem, and it was the Tango Icons extension for Thunderbird. It would crash even on Send/Recieve.

thanks for letting us know! :)

---

