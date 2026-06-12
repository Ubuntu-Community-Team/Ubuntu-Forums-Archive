---
title: "Issues connecting to Xen 4.2 on Ubuntu 13.04 with XenCenter 6.2"
date: 2013-09-04
forum: Virtualisation
---

### Post by Matt_Petersen on 2013-09-04
Fresh install of 13.04 Server fully updated with Xen 4.2 64bit hypervisor installed along with XCP-XAPI. 

I followed a couple of guides that mainly related to 4.1 and 12.04 so there were a couple of changes such as the Xend work around no longer being required, and a few file location differences but I eventually got everything installed and xenbr0 configured and working.

These were the two guides I followed [https://wiki.openstack.org/wiki/XenServer/Install/XcpXapiOnPrecise](https://wiki.openstack.org/wiki/XenServer/Install/XcpXapiOnPrecise) and [http://blog.scottlowe.org/2012/06/28/installing-xcp-xapi-on-ubuntu-server-12-04-lts/](http://blog.scottlowe.org/2012/06/28/installing-xcp-xapi-on-ubuntu-server-12-04-lts/)

I have tried to use XenCenter to manage Xen but when I attempt to login I get a password failure. I am using the same account that I used to install Xen so I know this account works ok at the Ubuntu level. The second guide I listed has a few comments in it about people also having similar login issues.

It looks like Xen and XAPI are running ok

root@ubuntux64:/var/log# xe host-list
uuid ( RO)                : daf31019-6548-6286-f45f-427c02d9da79
          name-label ( RW): ubuntux64
    name-description ( RW): Default install of XenServer

When I attempt a login and get a username or password error the xcp-xapi.log shows the following:

[20130904T20:53:56.324Z| info|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|xapi] Failed to locally authenticate user x64serveruser from HTTP request from Internet with User-Agent: XenCenter/6.2.0: Authentication failure
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|backtrace] Raised at xapi_session.ml:384.13-58 -> xapi_session.ml:36.12-17 -> xapi_session.ml:36.67-68 -> server_helpers.ml:79.11-41
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|dispatcher] Server_helpers.exec exception_handler: Got exception SESSION_AUTHENTICATION_FAILED: [ x64serveruser; Authentication failure ]
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|dispatcher] Raised at string.ml:150.25-34 -> stringext.ml:108.13-29
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|backtrace] Raised at string.ml:150.25-34 -> stringext.ml:108.13-29
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|xapi] Raised at server_helpers.ml:94.14-15 -> pervasiveext.ml:22.2-9
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|session.login_with_password D:ef5d450350d9|xapi] Raised at pervasiveext.ml:26.22-25 -> pervasiveext.ml:22.2-9
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|dispatch:session.login_with_password D:ea0966a6db4d|xapi] Raised at pervasiveext.ml:26.22-25 -> pervasiveext.ml:22.2-9
[20130904T20:54:01.329Z|debug|ubuntux64|132 INET 127.0.0.1:80|dispatch:session.login_with_password D:ea0966a6db4d|backtrace] Raised at pervasiveext.ml:26.22-25 -> server_helpers.ml:153.10-106 -> server.ml:478.19-183 -> server_helpers.ml:119.4-7
[20130904T20:54:02.205Z| info|ubuntux64|5 dbflush [/var/lib/xcp/state.db]||redo_log] Flushing database to all active redo-logs

This shows as an authentication failure but I can't understand why. I know the username and password works fine on the Ubuntu Server.

Thanks in advance for any help and sorry for such a length first post.

Update: Here is some more information. Looking at the auth logs I see the following:

Sep  5 17:16:10 ubuntux64 xapi: pam_succeed_if(xapi:auth): requirement "user ingroup root" not met by user "x64serveruser"

I added the user x64serveruser to the group root and now I can connect fine.....

Cheers
Matt.

---

