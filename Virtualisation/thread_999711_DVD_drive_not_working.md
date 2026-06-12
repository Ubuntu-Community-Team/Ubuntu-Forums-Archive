---
title: "DVD drive not working"
date: 2008-12-02
forum: Virtualisation
---

### Post by Dawei87 on 2008-12-02
I am using virtualbox to virtualize xp, and my dvd/cd drive only reads as CDrom. when i look at the properties of it it says i can burn dvds, but when i insert a dvd it wont play. at first i thought it was because i didnt have a dvd decoder, but i put one on with no luck. i am trying to use it to rip dvds and encode them, but when i try to open the disc in dvd decrypter it says there is an I/O error. when i enable passthrough it just says "initilising disc" for a very long time and never gets past that point. it can read the name of the disc and say it is a dvd when i look under my computer, but media play nor dvd decrypter will read it. can anyone help?

---

### Post by Dedoimedo on 2008-12-02
Is this dvd drive working normally, without virtualbox running?
Dedoimedo

---

### Post by Dawei87 on 2008-12-04
yes, it works in linux. and something very odd happened last night. i realized dma was disabled in my virtual windows xp, so i enabled it and restarted. and it worked perfectly after that. i never even shutdown since then, and today, it doesnt work anymore. i get the same I/O error as before. i just cant figure out what is wrong

---

