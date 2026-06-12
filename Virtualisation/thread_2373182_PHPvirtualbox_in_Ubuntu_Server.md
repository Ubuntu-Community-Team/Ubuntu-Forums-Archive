---
title: "PHPvirtualbox in Ubuntu Server"
date: 2017-10-03
forum: Virtualisation
---

### Post by ricardo35 on 2017-10-03
Hi,

Recently I did a clean install of an Ubuntu server with Samba. Everything is working perfectly.
Now I wanted to install PHPVirtualbox to create virtual machines.

I followed this guide:
[https://www.ostechnix.com/install-oracle-virtualbox-ubuntu-16-04-headless-server/](https://www.ostechnix.com/install-oracle-virtualbox-ubuntu-16-04-headless-server/)

The installation worked well until I try to login.

After entering my username and password it says: 
An error occurred communicating with your vboxwebsrv. No more requests will be sent by phpVirtualBox until the error is corrected and this page is refreshed. The details of this connection error should be displayed in a subsequent dialog box.

Then I press OK and the following error appears:

```
Exception Object(
    [message:protected] => Error logging in to vboxwebsrv.
    [string:Exception:private] => 
    [code:protected] => 64
    [file:protected] => /var/www/html/phpvirtualbox/endpoints/lib/vboxconnector.php
    [line:protected] => 220
    [trace:Exception:private] => Array
        (
            [0] => Array
                (
                    [file] => /var/www/html/phpvirtualbox/endpoints/lib/vboxconnector.php
                    [line] => 3374
                    [function] => connect
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                        )


                )


            [1] => Array
                (
                    [file] => /var/www/html/phpvirtualbox/endpoints/lib/vboxconnector.php
                    [line] => 951
                    [function] => remote_hostGetDetails
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                            [0] => 
                        )


                )


            [2] => Array
                (
                    [file] => /var/www/html/phpvirtualbox/endpoints/api.php
                    [line] => 316
                    [function] => __call
                    [class] => vboxconnector
                    [type] => ->
                    [args] => Array
                        (
                            [0] => hostGetDetails
                            [1] => Array
                                (
                                    [0] => 
                                    [1] => Array
                                        (
                                            [0] => Array
                                                (
                                                    [data] => Array
                                                        (
                                                            [responseData] => Array
                                                                (
                                                                )


                                                        )


                                                    [errors] => Array
                                                        (
                                                        )


                                                    [persist] => Array
                                                        (
                                                        )


                                                    [messages] => Array
                                                        (
                                                        )


                                                )


                                        )


                                )


                        )


                )


        )


    [previous:Exception:private] => 
)




Location:http://localhost:18083/
```

I've googled this but I can't find an answer nor do I know where to start with this.

I hope someone can help ?

---

### Post by deadflowr on 2017-10-03
*Thread moved to **Virtualization***

---

