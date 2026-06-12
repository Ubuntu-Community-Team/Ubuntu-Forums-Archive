---
title: "saving workspaces"
date: 2009-09-28
forum: Ubuntu Studio
---

### Post by c00kie55 on 2009-09-28
I cant figure this out.. how do i save my workspace or telling apps to open  on other workspaces(and remember its position)
this must be working becourse it the hole point about workspaces aint it ???

---

### Post by lovinglinux on 2009-09-28
You can save which applications are opened when you shut down by activating the option "Automatically remember running applications when logging out" in "System >> Preferences >> Startup Applications >> Options". Nevertheless, this won't remember which workspace each application was running. To do that you can use the compiz plugin "Place Window" to configure "Windows with fixed viewport" based on the application name. You must create a rule for each application, which will then open in the specified viewport (workspace) whenever you start it.

---

### Post by c00kie55 on 2009-09-28
Automatically remember running applications when logging out dont seams to work very well i just tryed with a lash project and and it didnt even remeber the lash_panel only thing working was firefox wich was running to... i like the way workspace is working ind fluxbox (rigth click a window send to a workspace rigth clik again tell it to remember position job done) mayby there is some way to get that working in ubuntu studio desktop without chansing the look and feel? (iam i dreaming (again)

i will try looking at compiz once again to se if can figure it out the way you sayd

anyway thanx

---

### Post by c00kie55 on 2009-09-28
I seam to be doing something wrong course every things still opens on desktop 1
in Windows with fixed viewport i only seams to be able to choose x and y positions 1-32 ?
hehe i feel stupid once again

---

### Post by lovinglinux on 2009-09-28
> **c00kie55 said:**
> I seam to be doing something wrong course every things still opens on desktop 1
in Windows with fixed viewport i only seams to be able to choose x and y positions 1-32 ?
hehe i feel stupid once again

Click the "+" button above the x/y positions. This will open the window grabber. Then click "grab" and click over the application window you want to configure to open in a particular desktop. You can also experiment with "Type" option. Then select "or" instead of "and" in the "Relation" option. This will fill the "Viewport positioned window" field with the proper code. You can also do that manually. For example, for Firefox I use **class=Firefox**.

Then you just need to change the x/y values. The values 1 and 1, means first desktop column and first desktop row, respectively.

---

### Post by c00kie55 on 2009-09-28
iam using karmic with studio on top maybe this aint working yet 

system>> Preferences >>CompisConfig Settings Manager>>Window Management>>Place Window.. there are to tabs General and Fixed Window Placement
 
in Fixed Window Placements i seams to be able to do as you say its just not working.

in General there is some rules maybe i have to play a little with them.

maybe i need some CompiZzz PluginZzz

---

### Post by c00kie55 on 2009-09-29
i just got this working now the problem was that i wasn't using virtual effects on the desktop or hardware drivers

thanx for the help

---

