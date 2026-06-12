---
title: "Legit Windows API implementation"
date: 2011-02-19
forum: Wine
---

### Post by Aerodynamite22 on 2011-02-19
If my understanding serves me right, you can use actual windows API in wine. But what meddling i have done with this area never usually ends well. so i was wondering if there was some sort of program where the user would point the program to a folder where windows has been installed (C:/) and then implement the .dll's and such from there.
Since this would require that one had windows installed, that would mean that there is no legal conflict there as well, right?

thanks for your response

---

### Post by Quadunit404 on 2011-02-19
I assume you mean pointing Wine at your actual Windows drive.

You should NEVER do that as Wine will overwrite ALL the Windows .dlls and .exes with its own and render Windows unable to boot without a complete reinstall. It's been done before and with disastrous results. Don't do it unless you want to spend hours or even weeks redoing everything on your computer.

---

