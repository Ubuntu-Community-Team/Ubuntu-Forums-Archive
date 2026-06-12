---
title: "Ubuntu Phone Staged and Windowed modes"
date: 2016-03-08
forum: Ubuntu Phone and Tablet
---

### Post by mike-parenti on 2016-03-08
[LEFT]I am running Ubuntu Stable 9.X on a Nexus 4. When I connect a bluetooth Keyboard/trackpad to the phone the software automatically switches to windowed mode. And after disconnecting the bluetooth keyboard/trackpad, the OS automatically switches back to staged mode. 

Today I ran the script  
**gsettings set [com.canonical]("http://www.google.com/url?q=http%3A%2F%2Fcom.canonical&sa=D&sntz=1&usg=AFQjCNEYui092CsdiKBtsxSsIODST3GQXA").Unity8 usage-mode Windowed** 
to manually put the OS in Windowed mode

And then moments later
[B][LEFT]gsettings set [com.canonical]("http://www.google.com/url?q=http%3A%2F%2Fcom.canonical&sa=D&sntz=1&usg=AFQjCNEYui092CsdiKBtsxSsIODST3GQXA").Unity8 usage-mode Staged
[/LEFT][/B][LEFT][LEFT]to manually put the OS in Staged mode[/LEFT][/LEFT]

And now when I connect the bluetooth keyboard/trackpad it doesn't switch automatically to Windowed mode. 
There must be another argument to get the phone back to switching automatically, right? 
[LEFT]**gsettings set [com.canonical]("http://www.google.com/url?q=http%3A%2F%2Fcom.canonical&sa=D&sntz=1&usg=AFQjCNEYui092CsdiKBtsxSsIODST3GQXA").Unity8 usage-mode** ????? 

Anyone else in this situation?[/LEFT]
[/LEFT]

---

### Post by mike-parenti on 2016-03-09
After multiple guesses I finally found it, "Automatic"

[B]gsettings set [com.canonical]("http://www.google.com/url?q=http%3A%2F%2Fcom.canonical&sa=D&sntz=1&usg=AFQjCNEYui092CsdiKBtsxSsIODST3GQXA").Unity8 usage-mode Automatic
[/B]
That's the command to run when you want to the phone to switch automatically between Staged and Windowed mode

:-)

---

### Post by WD_SeaSerpent on 2016-03-10
Thank you for useful infos! Do you mean "windowed" as landscape orientation and "staged" as portrait?

---

