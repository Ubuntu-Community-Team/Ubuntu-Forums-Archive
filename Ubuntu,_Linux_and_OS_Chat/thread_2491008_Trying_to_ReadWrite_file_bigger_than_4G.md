---
title: "Trying to Read/Write file bigger than 4G"
date: 2023-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by lalawawa on 2023-09-22
I've written a C++ program that, among other things, reads and creates files.

I'm using '::open64' to open the files, and '::lseek64' for seeking.  But there doesn't seem to be a '::read64' or '::write64' in '/usr/include/unistd.h' (the include where '::read' and ::write' live).

When I'm writing the file, 'write' stops one byte short of 4G.  I'm building with 'g++ -m64' so it's a 64-bit build.

How can I deal with files >4G?

I'm reading/writing one megabyte at a time.  The write that would make the output file exactly 4G long returns '(1 << 20) - 1' bytes written when it was told to write '1 << 20' bytes.

I looked at 'errno' after the failure and it's '2' which makes no sense, so it was not set by the write.

---

