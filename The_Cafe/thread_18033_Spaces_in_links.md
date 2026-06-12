---
title: "Spaces in links"
date: 2005-03-04
forum: The Cafe
---

### Post by Jonathan_ on 2005-03-04
I want to make a link to this program:

wine /home/username/.wine/drive_c/Program Files/Program/Program.exe

It doesnt like the space in 'Program Files' so how do I get round that? I thought adding %20 would work instead of the space but it doesnt like that :(

---

### Post by tim1 on 2005-03-04
You escape special characters with \

So it would be

wine /home/username/.wine/drive_c/Program\ Files/Program/Program.exe

You can also use "...", like

wine "/home/username/.wine/drive_c/Program Files/Program/Program.exe"

greets, tim

---

