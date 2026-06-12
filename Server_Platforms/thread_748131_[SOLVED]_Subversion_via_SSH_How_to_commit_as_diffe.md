---
title: "[SOLVED] Subversion via SSH: How to commit as different user? Issue with SVN config f"
date: 2008-04-07
forum: Server Platforms
---

### Post by HautingLu on 2008-04-07
I posted General Help, which may have been the wrong forum. I hoping someone here may point me in the right direction.....

User1 checks out some files from a remote server via ssh and creates a workspace. User1 has the same login on the remote server.

User2, who has access to User1's workspace, edits some files and wants to commit back to the server. User2 has the same login on the remote server.

Is it possible to User2 to commit as User2 so that the log history correctly shows that User2 made the commit?

I edited User2's subversion config file to read:

ssh = $SVN_SSH ssh -l User2

But when I go commit, it still asks for User1's password. From reading online, this should be possible, but for some reason the config file is not behaving as expected. I have some global ignores in the svn file, which **are** being ignored so svn seems to be functioning correctly.


Thanks.

---

### Post by HautingLu on 2008-04-07
I hope this helps someone in the future. Unresolved this would have caused me a major headache. For some reason, it was assumed that workspaces could be easily shared:

1. User2 needs sufficient permission to edit User1's workspace (rwx access I believe).

2. Edit ../User2/.subversion/config. Change the line that reads
#ssh = $SVN_SSH ssh to: 
> ssh = $SVN_SSH ssh -l <username>
<username> can be any user on the remote machine, but in my case it was User2.

3. This is what caused me the problems: checkout's. Checkouts were performed using: svn+ssh://User1@server/path/to/files when in fact it **should** have been > svn+ssh://server/path/to/files

**Not** specifying the user in the checkout command allows svn to use the -l <username> arg in the config file during commits of other's workspaces, which was my goal.


edit: on second thought, only Step 1 and Step 3 are really necessary. Step 2 is handy when ssh command needs to be modified (e.g. ssh -l <UserX> -p 555)

---

