---
title: "How to disassemble a simple binary file format?"
date: 2007-11-11
forum: The Cafe
---

### Post by blastus on 2007-11-11
I have a device that stores settings in a file that can be imported and exported. I need to send the file to the manufacturer of the device if there are settings I need changed that can't be done with the device. The issue is that because the file format is binary I cannot view it or manipulate it and I would like to be able to do just that instead of relying on the manufacturer and trusting that they changed the right setting for me.

The file is always 256KB and it appears to be encrypted because every time it is exported only the header of the file appears to remain the same. There is a sequence of 8 bytes in the header that changes everytime the file is exported and I think those bytes may be some sort of encryption key. The set of settings are static and most (if not all) of the settings are either boolean or int (there are no complex types or strings or anything like that.)

I thought that I could use a hex editor, export the file, change a setting, then export the file again and compare the difference but the entire file is different everytime. Then I thought I could export the file say ten times with the same settings and use some sort of program that tries to decrypt it and then compare the ten files again but I don't know how to do that.

At this point I am just trying to decipher the file such that everytime I export it I get results that I can compare. I'll worry about endianness and other stuff later. 

Where do I start?

Edit: Forgot to mention I'll use Java to aid in the process

---

### Post by LaRoza on 2007-11-11
Disassembling is using against the license. You can get disassemblers, but you would have to know assembly pretty well to make sense of it. You mentioned Java, that won't help a bit.

If it is encrypted, it is obviously illegal to disassemble. This thread should be closed...

---

### Post by bapoumba on 2007-11-11
Closing, thanks LaRoza.

---

