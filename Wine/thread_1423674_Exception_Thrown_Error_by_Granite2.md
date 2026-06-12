---
title: "Exception Thrown Error by Granite2"
date: 2010-03-06
forum: Wine
---

### Post by lordhedgehog on 2010-03-06
I'm trying to get Granite2 running under Ubuntu 8.10.  According to [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19322&iTestingId=50325") it works if you install dotnet20, d3dx9, gdiplus, and ole2 via winetricks.  I've installed those (and a few others), and the error message changed from a method not found error to this one:

```

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.Application ---> System.EntryPointNotFoundException: RegisterWindowMessage
  at (wrapper managed-to-native) System.Windows.Forms.SafeNativeMethods:RegisterWindowMessage (string)
  at System.Windows.Forms.Application..cctor () [0x00000] --- End of inner exception stack trace ---
  at Granite.b.a (System.Object A_0, System.Threading.ThreadExceptionEventArgs A_1) [0x00000] 
  at Granite.b.a (System.String[] A_0) [0x00000] 

```

I'm at a loss on how to proceed here.  I don't (think) I need a solution, but I'm not even sure where to fiddle with it now.  Ideas?

```

foo@bar:~/.wine/drive_c/Program Files/gran$ mono -V
Mono JIT compiler version 1.2.6 (tarball)
Copyright (C) 2002-2007 Novell, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none
foo@bar:~/.wine/drive_c/Program Files/gran$ wine --version
wine-1.1.39

```

---

