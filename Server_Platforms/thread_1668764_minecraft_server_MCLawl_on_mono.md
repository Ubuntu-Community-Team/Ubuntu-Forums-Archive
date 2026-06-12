---
title: "minecraft server MCLawl on mono"
date: 2011-01-16
forum: Server Platforms
---

### Post by Hiew on 2011-01-16
I'm attempting to run a server for a game (minecraft) however it requires mono. Now, the server is being managed by my hosting company though I have root access. I had to compile mono 2.8 in order for it to work on my system but I am still getting the following error and wasn't sure if anyone could at least just make sense of it.
```
----01/14/2011 11:34:09 ----
Type: DllNotFoundException
Source: System
Message: libMonoPosixHelper.so
Target: .ctor
Trace:   at (wrapper managed-to-native) System.IO.Compression.DeflateStream:CreateZStream (System.IO.Compression.CompressionMode,bool,System.IO.Compression.DeflateStream/UnmanagedReadOrWrite,intptr)
  at System.IO.Compression.DeflateStream..ctor (System.IO.Stream compressedStream, CompressionMode mode, Boolean leaveOpen, Boolean gzip) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.Compression.DeflateStream:.ctor (System.IO.Stream,System.IO.Compression.CompressionMode,bool,bool)
  at System.IO.Compression.GZipStream..ctor (System.IO.Stream compressedStream, CompressionMode mode, Boolean leaveOpen) [0x00000] in <filename unknown>:0 
  at System.IO.Compression.GZipStream..ctor (System.IO.Stream compressedStream, CompressionMode mode) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.Compression.GZipStream:.ctor (System.IO.Stream,System.IO.Compression.CompressionMode)
  at MCLawl.Level.Load (System.String givenName, Byte phys) [0x00000] in <filename unknown>:0 

-------------------------
----01/14/2011 11:34:09 ----
Type: NullReferenceException
Source: MCLawl_
Message: Object reference not set to an instance of an object
Target: <Start>b__0
Trace:   at MCLawl.Server.<Start>b__0 () [0x00000] in <filename unknown>:0 

-------------------------

```

---

### Post by directhex on 2011-01-17
> **Hiew said:**
> I'm attempting to run a server for a game (minecraft) however it requires mono. Now, the server is being managed by my hosting company though I have root access. I had to compile mono 2.8 in order for it to work on my system but I am still getting the following error and wasn't sure if anyone could at least just make sense of it.
```
----01/14/2011 11:34:09 ----
Type: DllNotFoundException
Source: System
Message: libMonoPosixHelper.so
Target: .ctor
Trace:   at (wrapper managed-to-native) System.IO.Compression.DeflateStream:CreateZStream (System.IO.Compression.CompressionMode,bool,System.IO.Compression.DeflateStream/UnmanagedReadOrWrite,intptr)
  at System.IO.Compression.DeflateStream..ctor (System.IO.Stream compressedStream, CompressionMode mode, Boolean leaveOpen, Boolean gzip) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.Compression.DeflateStream:.ctor (System.IO.Stream,System.IO.Compression.CompressionMode,bool,bool)
  at System.IO.Compression.GZipStream..ctor (System.IO.Stream compressedStream, CompressionMode mode, Boolean leaveOpen) [0x00000] in <filename unknown>:0 
  at System.IO.Compression.GZipStream..ctor (System.IO.Stream compressedStream, CompressionMode mode) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.Compression.GZipStream:.ctor (System.IO.Stream,System.IO.Compression.CompressionMode)
  at MCLawl.Level.Load (System.String givenName, Byte phys) [0x00000] in <filename unknown>:0 

-------------------------
----01/14/2011 11:34:09 ----
Type: NullReferenceException
Source: MCLawl_
Message: Object reference not set to an instance of an object
Target: <Start>b__0
Trace:   at MCLawl.Server.<Start>b__0 () [0x00000] in <filename unknown>:0 

-------------------------

```

The environment for your self-compiled Mono is incomplete. Ensure that the nonstandard path is added to /etc/ld.so.conf, and "ldconfig" run

---

### Post by Hiew on 2011-01-17
Okay I'm still new to this whole thing.

My /etc/ld.so.conf reads:
```
include ld.so.conf.d/*.conf
```

And I have mono.conf:

```
/etc/ld.so.conf.d/mono.conf
```

I also ran
```
ldconfig /etc/ld.so.conf.d/mono.conf
```

Doing this last step with ldconfig got rid of my errors, THANK YOU!

I've spent countless hours asking many people from a few different sources, and it was as simple as one line..

---

