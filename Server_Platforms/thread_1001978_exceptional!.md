---
title: "exceptional!"
date: 2008-12-04
forum: Server Platforms
---

### Post by Tohasu on 2008-12-04
Thanks to **directhex** on this forum, I got one of my earlier problems solved and have been able to successfully build the OpenSim software. Now when I try to run it (mono OpenSim.exe) I get the following which I think comes from my inexpert handling of the OpenSim.ini file. I assume I have to change the IP's in that file to the IP of the server I'm using. But it looks like a lot of the exceptions have to do with database management -- specifically SQLite

I've looked up URI (parent of URL) and have some vague idea I have to go to the ini file and supply some names - especially this "connection string."  My question is, am I on the right track here or is there more to it?  
  
And thanks! 


Exception: System.InvalidOperationException: Invalid connection string: no URI
at Mono.Data.SqliteClient.SqliteConnection.SetConnect ionString (System.String connstring) [0x00000] 
at Mono.Data.SqliteClient.SqliteConnection.set_Connec tionString (System.String value) [0x00000] 
at Mono.Data.SqliteClient.SqliteConnection..ctor (System.String connstring) [0x00000] 
at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteConnection:.ctor (string)
at OpenSim.Data.SQLite.SQLiteUserData.Initialise (System.String connect) [0x00000] 
at OpenSim.Framework.UserDataInitialiser.Initialise (IPlugin plugin) [0x00000] 
at OpenSim.Framework.PluginLoader`1[OpenSim.Framework.IUserDataPlugin].Load () [0x00000] 
at OpenSim.Framework.Communications.UserManagerBase.A ddPlugin (System.String provider, System.String connect) [0x00000] 
at OpenSim.OpenSimBase.InitialiseStandaloneServices (OpenSim.Framework.Communications.Cache.LibraryRoo tFolder libraryRootFolder) [0x00000] 
at OpenSim.OpenSimBase.StartupSpecific () [0x00000] 
at OpenSim.OpenSim.StartupSpecific () [0x00000] 
at OpenSim.Framework.Servers.BaseOpenSimServer.Startu p () [0x00000] 
at OpenSim.Application.Main (System.String[] args) [0x00000] 

Application is terminating: True

---

### Post by directhex on 2008-12-04
I don't have any OpenSim experience, but I think you're thinking along the right lines

You could try asking the OpenSim people if they can point in the right direction for mucking about with their ini file, right?

---

