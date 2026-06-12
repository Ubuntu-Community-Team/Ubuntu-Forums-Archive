---
title: "question"
date: 2009-06-19
forum: Wine
---

### Post by Meow27 on 2009-06-19
the game is navyfield, i think ive found a regression in wine 1.1.24

```
6
username@Phrozen-Box:~/.wine/drive_c/Program Files/SD EnterNET/NavyFIELD$ fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
wine: Unhandled page fault on read access to 0x00000000 at address 0x401441 (thread 001f), starting debugger...
flamehawk@Phrozen-Box:~/.wine/drive_c/Program Files/SD EnterNET/NavyFIELD$ 

```

what does this mean?

---

### Post by Meow27 on 2009-06-20
i still get the message when i start up, but after removing .wine and starting over again, i dont see any regression

---

### Post by Meow27 on 2009-06-20
yeah

i didnt have any errors in ./configure or make

i forgot to include that the game worked as it did since the last version of wine (unplayable, but loads)

---

