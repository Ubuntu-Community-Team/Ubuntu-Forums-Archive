---
title: "Dev Project Help: reading from wireless card and creating virtual ports"
date: 2009-10-23
forum: Ubuntu Dev Link Forum
---

### Post by joeldic on 2009-10-23
I am undertaking a development project and I'm not really sure where to start.

I have developed aplications in C/C++ before and have a fair knowledge about Unix, but I have never done any kernel or driver programming or anything low level like that before.

What I am trying to do is read the bit data from the wireless card, or any other port. I want to see the actual data that is coming into the card and then manipulate it - like interpreting the header data and extracting the data fields and things like that. I know that in Unix devices are treated like files, so that shouldn't be hard. I should be able to just pipe the raw data from the card file into a buffer and deal with it directly. I don't have any experience with this, so I don't really know where to start.

I also want to do something like that in reverse. So create a file that will mimic the data I would have streaming into a USB port, but make that file a 'virtual' USB port. So I can stream data into the file and make the cursor move or click, for example. 

I don't really know where to start with these ideas, so I'm looking for some high level advice about how to go about doing this. I have experience with C programming, but nothing low level like kernel or drivers.

Thanks.

---

