---
title: "Are &quot;viewports&quot; a deprecated feature?"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-14
Forgive me if I'm wrong here: I haven't fiddled with Unity, compiz and any UX/UI settings enough this cycle and am now taking some time to investigate, learn and compare our current state to what it was like in the recent past. 

Question: As far as I can see, there's no GUI place to set the number of viewports. Therefore unless a user installs ccsm, MyUnity, UnSettings, any other similar tweak tool, or directly edits dconf settings, the default is for all users to have a single desktop with no additional viewports. 

So I guess using viewports is deprecated - otherwise there would be ways to set it. And we know the cube is gone for a while.

Great, Windows has no viewports and people use it anyway, I can understand that although I really enjoy using viewports, but I can live with that. 

But the "Desktop Wall" plugin and its keyboard bindings are enabled and default. Desktop Wall is a viewport switcher, like the cube once was. 

Then what should I expect from this cycle / near future? Are viewports deprecated or not? 

Regards,
Effenberg

---

### Post by mc4man on 2012-09-14
not really - go ctrl+alt+arrow keys

What isn't available (yet??) is any default installed method to change WS setting or any compiz settings other than a small handful. Whether this is intentional or a wip of the move over to gsettings I have no idea.
(the history of unity suggests somewhere in between

Atm there are a few settings available in gcc & a couple in dconf (as seen in dconf-editor > org.compiz.intergated

So only thru making changes in ccsm will, for the most part, cause those changes to be added in dconf & visible. (generally org.compiz > profiles > unity >  plugins >* which can get settings added & editable but currently gets no schemas

So (as viewed here), if a compiz setting has a schema you change/add in dconf, if not then in ccsm & then it will show up in dconf & be editable. _They remain in dconf only while different than the default for that plugin/option_.

What the meaning of compiz > profiles > unity "plugins with set keys" I' not sure.

As an example mentioned before - 
To set a command which is in org.compiz.intergated,  I've found that if set in ccsm it will not take. So a command has to be entered in dconf where there is an offset 1=0 in ccsm, 2=1 in ccsm, ect.
Then once set in dconf it can be bound easier in ccsm

On the other - # of WS's, layout. These have to be set in ccsm, then they will show in dconf-editor as long as they are not the default value. If returned to defaults then they disappear from dconf - see screens 1 & 2  Screen 1 after I've altered in ccsm, (1x4), screen 2 after returning to the defaults, (2x2

Note: here I do use cube/rotate which works fine, The reason being I find rotate better suited to scroll on desktop which is my main method of switching viewports other than a certain command/dbus in use here also

---

