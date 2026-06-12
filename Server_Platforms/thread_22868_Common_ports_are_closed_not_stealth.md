---
title: "Common ports are closed not stealth"
date: 2005-03-30
forum: Server Platforms
---

### Post by Raija on 2005-03-30
I run some tests and all common ports were closed. I visited [www.grc.com](www.grc.com) and scan.sygatetech.com and the results were similar. Earlier ports were stelth. Only ping was open.  I have a basic installation 5.04 with all updates.
I run synaptic to get firestarter. Firestarter options were  "drop silently" and I stopped ping, but still ports are closed not stelth.
 Do I have to be worried?

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=Raija]I run some tests and all common ports were closed. I visited [www.grc.com](www.grc.com) and scan.sygatetech.com and the results were similar. Earlier ports were stelth. Only ping was open.  I have a basic installation 5.04 with all updates.
I run synaptic to get firestarter. Firestarter options were  "drop silently" and I stopped ping, but still ports are closed not stelth.
 Do I have to be worried?[/QUOTE]
 I did it myself. Only port 22 (ssh) was open (intended). What ports are closed and what non-standard services do you run ?

---

### Post by Raija on 2005-03-30
Ports closed: 0, 21, 22, 23, 25, 79, 80, 110, 113, 119, 135, 139, 143, 389, 443, 445, 1002, 1024, 1025, 1026, 1027, 1028, 1029, 1030, 1720, 5000.
I don't run any non-standard services.

---

### Post by Raija on 2005-03-30
Problem solved!

 I have played with Evolution mail. Now I put it back to normal options (never use a secret connection) and my ports are stealthed again.

Thanks! Helped a lot to know that everybody else don't have the same problem.

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=Raija]Problem solved!

 I have played with Evolution mail. Now I put it back to normal options (never use a secret connection) and my ports are stealthed again.

Thanks! Helped a lot to know that everybody else don't have the same problem.[/QUOTE]
 np :)

What strange setting did cause the problem ? secret connection????

And what was the purpose of the setting ?

---

### Post by Raija on 2005-03-30
[QUOTE=demon666_nl]np :)

What strange setting did cause the problem ? secret connection????

And what was the purpose of the setting ?[/QUOTE]

Sorry, my Finnish to English translation. The current word is secure.

When the ports were closed I have done so:
Evolution mail, edit/preferenses, receiving Email, Security/ Use secure connection
and finally Whenever Possible. 
I change it back to Never and ports are stealth again.

Maybe I was too curious.

---

### Post by ubuntu_demon on 2005-03-30
:)

---

