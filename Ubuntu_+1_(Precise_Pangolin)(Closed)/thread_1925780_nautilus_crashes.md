---
title: "nautilus crashes"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bmbaker on 2012-02-15
nautilus crashes as soon as you try to open a folder !
bug reported here 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/932627](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/932627)

---

### Post by dino99 on 2012-02-15
not mine :)

---

### Post by bmbaker on 2012-02-15
seems it was nautilus dropbox causing the crash

```
bb@Dream-Test:~$ nautilus
Initializing nautilus-dropbox 0.7.1

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_background_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_item_list_free: assertion `item_list != NULL' failed

** CRITICAL **: nautilus_menu_provider_get_file_items: assertion `NAUTILUS_IS_MENU_PROVIDER (provider)' failed
GLib (gthread-posix.c): Unexpected error from C library during 'Invalid argument': pthread_cond_timedwait.  Aborting.
Aborted (core dumped))
```

---

