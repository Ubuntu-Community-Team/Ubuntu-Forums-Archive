---
title: "Thanks! and Spontaneous Close of Thunderbird-2 and Firefox-2"
date: 2008-02-04
forum: Ubuntuzilla
---

### Post by mlnease on 2008-02-04
Hello,

First of all, thanks a million--yesterday I installed Thunderbird-2 and Firefox-2 (into 6.06.1, 686 kernal) using the command line instructions at [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) and both worked like a charm--after numerous wasted attempts by other means.

Both are working fine now except that, for no apparent reason, each app closes spontaneously in the background, fairly often.  I've checked the threads and haven't seen this problem.  I'm actually happy enough with these new versions to live with this bug but if anyone has any suggestions I'd be most grateful.

Thanks again for all the good work.

mike

---

### Post by nanotube on 2008-02-05
hm, here are a couple of things to try.

first, try starting your firefox (or thunderbird) from a terminal, and keep that terminal window open, and wait for the program to "spontaneously" close itself. then see if there are any interesting diagnostic messages left over. 

another thing to try, for thunderbird: start composing a new "dummy" message, then just minimize it and forget about it. see if thunderbird still spontaneously closes, or if the dialog "do you want to discard this message" prevents it from closing.

other than that, i have to say i haven't come across this behavior before, so i can't offer any quick fixes for now. :)

---

### Post by mlnease on 2008-02-05
> **nanotube said:**
> hm, here are a couple of things to try.

first, try starting your firefox (or thunderbird) from a terminal, and keep that terminal window open, and wait for the program to "spontaneously" close itself. then see if there are any interesting diagnostic messages left over. 

another thing to try, for thunderbird: start composing a new "dummy" message, then just minimize it and forget about it. see if thunderbird still spontaneously closes, or if the dialog "do you want to discard this message" prevents it from closing.

other than that, i have to say i haven't come across this behavior before, so i can't offer any quick fixes for now. :)

Aha--gremlin traps!  I've set both and will keep you posted as to any results--thanks again--

mike

---

### Post by mlnease on 2008-02-05
> **nanotube said:**
> hm, here are a couple of things to try.

first, try starting your firefox (or thunderbird) from a terminal, and keep that terminal window open, and wait for the program to "spontaneously" close itself. then see if there are any interesting diagnostic messages left over. 

another thing to try, for thunderbird: start composing a new "dummy" message, then just minimize it and forget about it. see if thunderbird still spontaneously closes, or if the dialog "do you want to discard this message" prevents it from closing.

other than that, i have to say i haven't come across this behavior before, so i can't offer any quick fixes for now. :)

OK, results from trap #1:

mn@ubuntu:~$ firefox
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception
[NoScript] [NoScript] external load intercepted
/opt/firefox/run-mozilla.sh: line 131:  5506 Killed                  "$prog" ${1 +"$@"}
mn@ubuntu:~$

---

### Post by nanotube on 2008-02-23
hm, sorry, i am out of ideas here... could be some extensions causing trouble? see if that happens still if you run firefox (or thunderbird) with a fresh empty profile, without anything in it. ...

---

### Post by mlnease on 2008-02-23
> **nanotube said:**
> hm, sorry, i am out of ideas here... could be some extensions causing trouble? see if that happens still if you run firefox (or thunderbird) with a fresh empty profile, without anything in it. ...

Thanks, Nano--I've tried removing all extensions together and severally and the results haven't varied.

I've also tried a fresh empty profile in Thunderbird but not in Firefox--guess I'll try that next.  Thanks for thinking of me Mate and

Cheers,

mn

---

### Post by mazsi on 2008-09-03
Hi! I changed my thunderbird theme from gnome to azerty  and i downloaded and installed ubuntuzilla program. And this was the answer by my spontaneous close. Try the theme change. Have a nice day!

---

### Post by mlnease on 2008-09-03
> **mazsi said:**
> Hi! I changed my thunderbird theme from gnome to azerty  and i downloaded and installed ubuntuzilla program. And this was the answer by my spontaneous close. Try the theme change. Have a nice day!

Hello and Thanks,

Haven't had this problem since I last reinstalled Hardy, but azerty, eh?  Hadn't heard of it before, I'll make a note of it and thanks again for the response.

mike

---

