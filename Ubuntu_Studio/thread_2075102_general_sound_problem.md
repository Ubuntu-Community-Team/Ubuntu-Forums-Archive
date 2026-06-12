---
title: "general sound problem"
date: 2012-10-23
forum: Ubuntu Studio
---

### Post by StevieBread on 2012-10-23
Hi there,

I'm running Ubuntu Studio 12.10
Strange things happen:
1. After login, playing mp3 or videos -> sound is ok.
2. Then I start Ardour, work with a project -> sound is ok
3. Then I exit Ardour, playing mp3 or videos -> NO SOUND!!

(4.) Starting Ardour again -> sound still works

This is reproducible with every boot.

Any idea what to do?

---

### Post by jejeman on 2012-10-23
After quiting Ardour is JACK really dead?

---

### Post by sgx on 2012-10-23
> **StevieBread said:**
> Hi there,

I'm running Ubuntu Studio 12.10
Strange things happen:
1. After login, playing mp3 or videos -> sound is ok.
2. Then I start Ardour, work with a project -> sound is ok
3. Then I exit Ardour, playing mp3 or videos -> NO SOUND!!

(4.) Starting Ardour again -> sound still works

This is reproducible with every boot.

Any idea what to do?
If jackd is not terminated, you can use Aqualung,
a jackd media player, or vlc/xmms/xine if their jackd plugins are installed.

killall jackd

that command will tell you if jackd was not running,
and kill it without comment, if it was running.
Cheers

---

### Post by StevieBread on 2012-10-24
@jejeman:
@sgx:
Thanks for your answers. 
Yes, you were right - jackd was not killed correctly. Killing the process manually helps.
Yesterday I booted the system directly from the Ubuntu studio 12.10 DVD and it worked fine - jackd is killed after terminiating Ardour, so it seems to be a problem of my harddisk installation.

---

