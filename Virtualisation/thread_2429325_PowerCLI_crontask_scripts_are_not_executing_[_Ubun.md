---
title: "PowerCLI crontask scripts are not executing [ Ubuntu 16.04 ]"
date: 2019-10-16
forum: Virtualisation
---

### Post by mikeaw2010 on 2019-10-16
Typing this from my phone and will edit when I can to properly implement the code brackets.

In short, I have a crontask set to create a snapshot of a VM via PowerCLI but when executing the job, the only thing I receive from cron is "PowerShell console is ready for user input". Its like its opening the powershell but not executing the script for some reason.

Below is the script:
======================
#! /usr/bin/pwsh

 

Connect-VIServer -Server x.x.x.x-User xxxx -Password xxxxxxxx

$date = Get-Date

New-Snapshot -VM xxxxxxxx -Name "apt-mirror-snapshot-$date"

Get-VM xxxxxxxx | Get-Snapshot |

Where-Object {$_.Created -lt (Get-Date).AddMonths(-2)} |

 

Sort-Object -Property Created |

 

Remove-Snapshot -Confirm:$false -RemoveChildren
======================

And below are the syslogs

 ======================
Oct 16 16:58:01 CRON[15671]: (root) CMD (/home/user/scripts/mirror/mirror-snapshots)

Oct 16 16:58:01 powershell[15672]: (6.2.3:1:80) [Perftrack_ConsoleStartupStart:PowershellConsoleStartup.WinStart.Informational] PowerShell console is starting up

Oct 16 16:58:01 powershell[15672]: (6.2.3:6:80) [NamedPipeIPC_ServerListenerStarted:NamedPipe.Open.Informational] Windows PowerShell has started an IPC listening thread on process: 15672 in AppDomain: None.

Oct 16 16:58:01 powershell[15672]: (6.2.3:1:80) [Perftrack_ConsoleStartupStop:PowershellConsoleStartup.WinStop.Informational] PowerShell console is ready for user input

Oct 16 16:58:02 postfix/pickup[15193]: 82B1652031E: uid=0 from=<root>

Oct 16 16:58:02 postfix/cleanup[15690]: 82B1652031E: message-id=<20191016215802.82B1652031E@cec-esxi-mgmt>

Oct 16 16:58:02 postfix/qmgr[14472]: 82B1652031E: from=<root@*******>, size=2012, nrcpt=1 (queue active)

Oct 16 16:58:02 postfix/local[15692]: 82B1652031E: to=<root@*******>, orig_to=<root>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)

Oct 16 16:58:02 postfix/qmgr[14472]: 82B1652031E: removed
======================

Any idea as to what's going on?

Thanks.

---

