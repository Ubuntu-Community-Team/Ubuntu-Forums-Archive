---
title: "Long boot time"
date: 2009-02-18
forum: Server Platforms
---

### Post by tlindvall on 2009-02-18
Hello,

I've installed ubuntu server 8.10 x86_64.  System works fine after boot, but boottime is several minutes.  I browsed through logs and found a lot of timed out messages from different devices for ex:

Feb 17 19:29:09 serveri kernel: [  336.091491] modprobe      D ffffffff80234069     0  3343   3342
Feb 17 19:29:09 serveri kernel: [  336.091494]  ffff88003ccb3ca8 0000000000000086 ffff88003dccfe10 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.091498]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091502]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091505] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.091510]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091514]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.091517]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091522]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.091525]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.091529]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.091532]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.091535]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091544]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091549]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.091552]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.091559]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091565]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.091572]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091578]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091585]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091590]  [<ffffffffa0502023>] alsa_card_via82xx_init+0x23/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091593]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.091597]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091605]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091608]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
F

Any idea what's wrong?

Regs Tarmo

---

### Post by Mr.Carramba on 2009-02-18
did you get same message if you reboot again?
if so try to reinstall soundcard driver (alsa) 

Regards

---

### Post by tlindvall on 2009-02-18
Thanks for your answer.  I get these messages in every boot and  I get these from bunch of drivers.  I list all of them below.  Could you tell me what packages should I reinstall with apt-get?  Has this anything to do with kernel update done by update daemon?

Regs Tarmo

********************************************************

Feb 17 19:27:31 serveri kernel: [  198.650118] khubd         D ffffffff80234069     0  1310      2
Feb 17 19:27:31 serveri kernel: [  198.650123]  ffff880037893760 0000000000000046 0000000000000000 ffff88003cf950c0
Feb 17 19:27:31 serveri kernel: [  198.650128]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.650133]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.650137] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.650167]  [<ffffffff80501ef5>] __mutex_lock_slowpath+0x85/0xd0
Feb 17 19:27:31 serveri kernel: [  198.650173]  [<ffffffff80501c79>] ? mutex_unlock+0x9/0x20
Feb 17 19:27:31 serveri kernel: [  198.650177]  [<ffffffff80501c63>] mutex_lock+0x13/0x20
Feb 17 19:27:31 serveri kernel: [  198.650189]  [<ffffffffa0273a61>] i2c_add_adapter+0x41/0xc0 [i2c_core]
Feb 17 19:27:31 serveri kernel: [  198.650198]  [<ffffffffa0496f88>] dvb_usb_i2c_init+0x98/0xe0 [dvb_usb]
Feb 17 19:27:31 serveri kernel: [  198.650205]  [<ffffffffa04968a2>] dvb_usb_init+0x92/0x110 [dvb_usb]
Feb 17 19:27:31 serveri kernel: [  198.650211]  [<ffffffffa0496b1e>] dvb_usb_device_init+0x1fe/0x2e0 [dvb_usb]
Feb 17 19:27:31 serveri kernel: [  198.650221]  [<ffffffffa04b6025>] dibusb_mc_probe+0x25/0x28 [dvb_usb_dibusb_mc]
Feb 17 19:27:31 serveri kernel: [  198.650246]  [<ffffffffa013878c>] usb_probe_interface+0xcc/0x180 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650254]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:27:31 serveri kernel: [  198.650259]  [<ffffffff80431002>] really_probe+0x72/0x1a0
Feb 17 19:27:31 serveri kernel: [  198.650262]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:27:31 serveri kernel: [  198.650267]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:27:31 serveri kernel: [  198.650271]  [<ffffffff80431180>] driver_probe_device+0x50/0x60
Feb 17 19:27:31 serveri kernel: [  198.650274]  [<ffffffff8043122e>] __device_attach+0xe/0x10
Feb 17 19:27:31 serveri kernel: [  198.650278]  [<ffffffff804303cb>] bus_for_each_drv+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.650281]  [<ffffffff804312f8>] device_attach+0x88/0x90
Feb 17 19:27:31 serveri kernel: [  198.650286]  [<ffffffff804301b5>] bus_attach_device+0x55/0x80
Feb 17 19:27:31 serveri kernel: [  198.650289]  [<ffffffff8042eb9a>] device_add+0x3da/0x4b0
Feb 17 19:27:31 serveri kernel: [  198.650294]  [<ffffffff80234069>] ? __phys_addr+0x9/0x50
Feb 17 19:27:31 serveri kernel: [  198.650309]  [<ffffffffa0137378>] usb_set_configuration+0x4a8/0x640 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650313]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:27:31 serveri kernel: [  198.650330]  [<ffffffffa014060b>] generic_probe+0x3b/0xb0 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650335]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:27:31 serveri kernel: [  198.650349]  [<ffffffffa0137742>] usb_probe_device+0x42/0x50 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650353]  [<ffffffff80431002>] really_probe+0x72/0x1a0
Feb 17 19:27:31 serveri kernel: [  198.650358]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:27:31 serveri kernel: [  198.650362]  [<ffffffff80431180>] driver_probe_device+0x50/0x60
Feb 17 19:27:31 serveri kernel: [  198.650365]  [<ffffffff8043122e>] __device_attach+0xe/0x10
Feb 17 19:27:31 serveri kernel: [  198.650369]  [<ffffffff804303cb>] bus_for_each_drv+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.650372]  [<ffffffff804312f8>] device_attach+0x88/0x90
Feb 17 19:27:31 serveri kernel: [  198.650377]  [<ffffffff804301b5>] bus_attach_device+0x55/0x80
Feb 17 19:27:31 serveri kernel: [  198.650380]  [<ffffffff8042eb9a>] device_add+0x3da/0x4b0
Feb 17 19:27:31 serveri kernel: [  198.650395]  [<ffffffffa0137ff0>] ? usb_autopm_do_device+0xc0/0x110 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650410]  [<ffffffffa0130c4f>] usb_new_device+0x6f/0xd0 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650425]  [<ffffffffa0131730>] hub_port_connect_change+0x510/0xad0 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650440]  [<ffffffffa013527a>] ? usb_free_urb+0x1a/0x20 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650443]  [<ffffffff80234069>] ? __phys_addr+0x9/0x50
Feb 17 19:27:31 serveri kernel: [  198.650458]  [<ffffffffa0136554>] ? usb_control_msg+0xf4/0x110 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650473]  [<ffffffffa0132103>] hub_events+0x2e3/0x650 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650488]  [<ffffffffa01324b5>] hub_thread+0x45/0x190 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650493]  [<ffffffff80266fd0>] ? autoremove_wake_function+0x0/0x40
Feb 17 19:27:31 serveri kernel: [  198.650507]  [<ffffffffa0132470>] ? hub_thread+0x0/0x190 [usbcore]
Feb 17 19:27:31 serveri kernel: [  198.650511]  [<ffffffff80266b9e>] kthread+0x4e/0x90
Feb 17 19:27:31 serveri kernel: [  198.650514]  [<ffffffff80213c99>] child_rip+0xa/0x11
Feb 17 19:27:31 serveri kernel: [  198.650518]  [<ffffffff80266b50>] ? kthread+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.650521]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
Feb 17 19:27:31 serveri kernel: [  198.650522] 
Feb 17 19:27:31 serveri kernel: [  198.650631] modprobe      D ffffffff80234069     0  2905   2904
Feb 17 19:27:31 serveri kernel: [  198.650635]  ffff88003bd55ca8 0000000000000082 ffff88003e042808 ffff880001017470
Feb 17 19:27:31 serveri kernel: [  198.650640]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.650644]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.650648] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.650653]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.650659]  [<ffffffff802473fe>] ? try_to_wake_up+0x11e/0x2e0
Feb 17 19:27:31 serveri kernel: [  198.650662]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.650667]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.650671]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.650674]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.650678]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.650683]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.650689]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:27:31 serveri kernel: [  198.650694]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.650697]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.650703]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:27:31 serveri kernel: [  198.650709]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.650715]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:27:31 serveri kernel: [  198.650721]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.650727]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:27:31 serveri kernel: [  198.650732]  [<ffffffffa01a6023>] flexcop_pci_module_init+0x23/0x25 [b2c2_flexcop_pci]
Feb 17 19:27:31 serveri kernel: [  198.650736]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.650740]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.650747]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.650752]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.650754] 
Feb 17 19:27:31 serveri kernel: [  198.650863] modprobe      D ffffffff80234069     0  2911   2910
Feb 17 19:27:31 serveri kernel: [  198.650867]  ffff88003bc61ca8 0000000000000082 ffffffff803a7b99 ffff880001017470
Feb 17 19:27:31 serveri kernel: [  198.650871]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.650876]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.650879] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.650884]  [<ffffffff803a7b99>] ? rb_insert_color+0x109/0x140
Feb 17 19:27:31 serveri kernel: [  198.650890]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.650894]  [<ffffffff802473fe>] ? try_to_wake_up+0x11e/0x2e0
Feb 17 19:27:31 serveri kernel: [  198.650897]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.650902]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.650905]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.650909]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.650912]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.650916]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.650925]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:27:31 serveri kernel: [  198.650930]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.650934]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.650941]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:27:31 serveri kernel: [  198.650947]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.650954]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:27:31 serveri kernel: [  198.650959]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.650967]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:27:31 serveri kernel: [  198.650973]  [<ffffffffa032381a>] cx8800_init+0x3a/0x40 [cx8800]
Feb 17 19:27:31 serveri kernel: [  198.650976]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.650980]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.650987]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.650991]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.650993] 
Feb 17 19:27:31 serveri kernel: [  198.651101] modprobe      D ffffffff80234069     0  2913   2912
Feb 17 19:27:31 serveri kernel: [  198.651105]  ffff88003bd35ca8 0000000000000086 ffff88003e4e80a0 0000000000000000
Feb 17 19:27:31 serveri kernel: [  198.651109]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651113]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651117] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.651122]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651126]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:27:31 serveri kernel: [  198.651129]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651134]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.651137]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.651141]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.651144]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.651148]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651154]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:27:31 serveri kernel: [  198.651159]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.651162]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.651168]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:27:31 serveri kernel: [  198.651174]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.651180]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:27:31 serveri kernel: [  198.651185]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651191]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:27:31 serveri kernel: [  198.651196]  [<ffffffffa0455d0a>] cx88_audio_init+0x3a/0x3c [cx88_alsa]
Feb 17 19:27:31 serveri kernel: [  198.651199]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.651203]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.651209]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.651213]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.651215] 
Feb 17 19:27:31 serveri kernel: [  198.651323] modprobe      D ffffffff80234069     0  2915   2914
Feb 17 19:27:31 serveri kernel: [  198.651327]  ffff88003e0c9ca8 0000000000000082 ffff88003e0973c0 ffff880001017470
Feb 17 19:27:31 serveri kernel: [  198.651331]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651336]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651339] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.651344]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651348]  [<ffffffff802473fe>] ? try_to_wake_up+0x11e/0x2e0
Feb 17 19:27:31 serveri kernel: [  198.651352]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651356]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.651360]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.651363]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.651367]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.651370]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651377]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:27:31 serveri kernel: [  198.651382]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.651385]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.651392]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:27:31 serveri kernel: [  198.651397]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.651403]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:27:31 serveri kernel: [  198.651408]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651414]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:27:31 serveri kernel: [  198.651420]  [<ffffffffa032e4ba>] cx8802_init+0x3a/0x40 [cx8802]
Feb 17 19:27:31 serveri kernel: [  198.651423]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.651427]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.651433]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.651437]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.651439] 
Feb 17 19:27:31 serveri kernel: [  198.651567] modprobe      D ffffffff80234069     0  3017   3016
Feb 17 19:27:31 serveri kernel: [  198.651571]  ffff88003e003c68 0000000000000082 ffff8800378635f0 0000000000000000
Feb 17 19:27:31 serveri kernel: [  198.651575]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651579]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651583] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.651588]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651592]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:27:31 serveri kernel: [  198.651595]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651600]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.651603]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.651607]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.651610]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.651614]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651619]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.651622]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.651628]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.651635]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651643]  [<ffffffffa01ae3a1>] parport_pc_find_ports+0xda/0x114 [parport_pc]
Feb 17 19:27:31 serveri kernel: [  198.651650]  [<ffffffffa01ae481>] parport_pc_init+0xa6/0xab [parport_pc]
Feb 17 19:27:31 serveri kernel: [  198.651657]  [<ffffffffa01ae3db>] ? parport_pc_init+0x0/0xab [parport_pc]
Feb 17 19:27:31 serveri kernel: [  198.651669]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.651673]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.651680]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.651684]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.651686] 
Feb 17 19:27:31 serveri kernel: [  198.651823] modprobe      D ffffffff80234069     0  3293   3292
Feb 17 19:27:31 serveri kernel: [  198.651826]  ffff88003bd77ca8 0000000000000086 ffff88003e47bd70 0000000000000000
Feb 17 19:27:31 serveri kernel: [  198.651830]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651835]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.651839] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.651843]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651847]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:27:31 serveri kernel: [  198.651851]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651855]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.651859]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.651862]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.651866]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.651869]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.651874]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:27:31 serveri kernel: [  198.651879]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.651883]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.651888]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:27:31 serveri kernel: [  198.651894]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.651899]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:27:31 serveri kernel: [  198.651904]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.651909]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:27:31 serveri kernel: [  198.651913]  [<ffffffffa01b6023>] i2c_vt596_init+0x23/0x25 [i2c_viapro]
Feb 17 19:27:31 serveri kernel: [  198.651917]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.651921]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.651927]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.651931]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.651933] 
Feb 17 19:27:31 serveri kernel: [  198.652074] modprobe      D ffffffff80234069     0  3307   3306
Feb 17 19:27:31 serveri kernel: [  198.652077]  ffff88003e477ca8 0000000000000082 ffff88003e957780 0000000000000000
Feb 17 19:27:31 serveri kernel: [  198.652082]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.652086]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.652090] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.652095]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.652099]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:27:31 serveri kernel: [  198.652102]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.652107]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.652110]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.652114]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.652117]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.652121]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.652127]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:27:31 serveri kernel: [  198.652132]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.652136]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.652141]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:27:31 serveri kernel: [  198.652147]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.652153]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:27:31 serveri kernel: [  198.652158]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.652163]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:27:31 serveri kernel: [  198.652168]  [<ffffffffa04ee023>] alsa_card_via82xx_init+0x23/0x25 [snd_via82xx_modem]
Feb 17 19:27:31 serveri kernel: [  198.652172]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.652176]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.652182]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.652186]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.652188] 
Feb 17 19:27:31 serveri kernel: [  198.652325] modprobe      D ffffffff80234069     0  3337   3336
Feb 17 19:27:31 serveri kernel: [  198.652329]  ffff88003dd6dca8 0000000000000082 ffff88003cca5550 0000000000000000
Feb 17 19:27:31 serveri kernel: [  198.652333]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.652338]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.652341] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.652346]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.652350]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:27:31 serveri kernel: [  198.652354]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.652358]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.652362]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.652365]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.652368]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.652372]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.652377]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:27:31 serveri kernel: [  198.652381]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.652385]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.652390]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:27:31 serveri kernel: [  198.652395]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.652400]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:27:31 serveri kernel: [  198.652405]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.652410]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:27:31 serveri kernel: [  198.652414]  [<ffffffffa0509023>] k8temp_init+0x23/0x25 [k8temp]
Feb 17 19:27:31 serveri kernel: [  198.652417]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.652421]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.652427]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.652431]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.652433] 
Feb 17 19:27:31 serveri kernel: [  198.652571] modprobe      D ffffffff80234069     0  3343   3342
Feb 17 19:27:31 serveri kernel: [  198.652575]  ffff88003ccb3ca8 0000000000000086 ffff88003dccfe10 0000000000000000
Feb 17 19:27:31 serveri kernel: [  198.652579]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.652584]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:27:31 serveri kernel: [  198.652587] Call Trace:
Feb 17 19:27:31 serveri kernel: [  198.652592]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:27:31 serveri kernel: [  198.652596]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:27:31 serveri kernel: [  198.652600]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:27:31 serveri kernel: [  198.652604]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:27:31 serveri kernel: [  198.652608]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:27:31 serveri kernel: [  198.652611]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:27:31 serveri kernel: [  198.652614]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:27:31 serveri kernel: [  198.652618]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:27:31 serveri kernel: [  198.652626]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:27:31 serveri kernel: [  198.652631]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:27:31 serveri kernel: [  198.652634]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:27:31 serveri kernel: [  198.652640]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:27:31 serveri kernel: [  198.652646]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:27:31 serveri kernel: [  198.652652]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:27:31 serveri kernel: [  198.652657]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:27:31 serveri kernel: [  198.652669]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:27:31 serveri kernel: [  198.652674]  [<ffffffffa0502023>] alsa_card_via82xx_init+0x23/0x25 [snd_via82xx]
Feb 17 19:27:31 serveri kernel: [  198.652677]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:27:31 serveri kernel: [  198.652681]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:27:31 serveri kernel: [  198.652688]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:27:31 serveri kernel: [  198.652692]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:27:31 serveri kernel: [  198.652694] 
Feb 17 19:27:31 serveri kernel: [  214.637564] loop: module loaded
Feb 17 19:27:31 serveri kernel: [  214.684345] lp0: using parport0 (interrupt-driven).
Feb 17 19:27:31 serveri kernel: [  216.472447] Adding 2184832k swap on /dev/sdb2.  Priority:-1 extents:1 across:2184832k
Feb 17 19:27:31 serveri kernel: [  217.171015] EXT3 FS on sdb1, internal journal
Feb 17 19:27:31 serveri kernel: [  221.261454] type=1505 audit(1234891634.549:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4699
Feb 17 19:27:31 serveri kernel: [  221.818766] type=1505 audit(1234891635.099:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4704
Feb 17 19:27:31 serveri kernel: [  221.819027] type=1505 audit(1234891635.099:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4704
Feb 17 19:27:31 serveri kernel: [  222.016846] type=1505 audit(1234891635.299:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4708
Feb 17 19:27:31 serveri kernel: [  222.378311] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 17 19:27:31 serveri kernel: [  222.892206] skge eth0: enabling interface
Feb 17 19:27:31 serveri kernel: [  224.205173] NET: Registered protocol family 17
Feb 17 19:27:31 serveri kernel: [  225.472218] skge eth0: Link is up at 1000 Mbps, full duplex, flow control both
Feb 17 19:27:31 serveri kernel: [  229.960249] NET: Registered protocol family 10
Feb 17 19:27:31 serveri kernel: [  229.960770] lo: Disabled Privacy Extensions
Feb 17 19:27:31 serveri kernel: [  230.711998] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
Feb 17 19:27:31 serveri kernel: [  233.127972] ACPI: WMI: Mapper loaded
Feb 17 19:27:31 serveri kernel: [  236.221712] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 2800+ processors (1 cpu cores) (version 2.20.00)
Feb 17 19:27:31 serveri kernel: [  236.221755] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x2
Feb 17 19:27:31 serveri kernel: [  236.221758] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0xa
Feb 17 19:27:37 serveri kernel: [  243.863023] ppdev: user-space parallel port driver
Feb 17 19:27:38 serveri kernel: [  245.038553] Bridge firewalling registered
Feb 17 19:27:38 serveri kernel: [  245.055257] vnet0: starting userspace STP failed, starting kernel STP
Feb 17 19:27:38 serveri kernel: [  245.494691] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
Feb 17 19:27:38 serveri kernel: [  245.494859] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
Feb 17 19:27:38 serveri kernel: [  245.494861] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Feb 17 19:27:38 serveri kernel: [  245.494864] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Feb 17 19:27:49 serveri kernel: [  256.089161] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 17 19:27:49 serveri kernel: [  256.599470] [drm] Initialized drm 1.1.0 20060810
Feb 17 19:27:49 serveri kernel: [  256.639785] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Feb 17 19:27:50 serveri kernel: [  257.235206] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
Feb 17 19:27:50 serveri kernel: [  257.235233] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Feb 17 19:27:50 serveri kernel: [  257.235339] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Feb 17 19:27:50 serveri kernel: [  257.484180] [drm] Setting GART location based on new memory map
Feb 17 19:27:50 serveri kernel: [  257.484192] [drm] Loading R200 Microcode
Feb 17 19:27:50 serveri kernel: [  257.484259] [drm] writeback test succeeded in 1 usecs
Feb 17 19:28:50 serveri kernel: [  317.254734] ecryptfs_parse_options: eCryptfs: unrecognized option 'rw'
Feb 17 19:28:50 serveri kernel: [  317.254745] ecryptfs_parse_options: eCryptfs: unrecognized option 'user=niko'
Feb 17 19:28:52 serveri pulseaudio[6757]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 17 19:28:52 serveri pulseaudio[6761]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Toiminto ei ole sallittu
Feb 17 19:28:52 serveri pulseaudio[6761]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Toiminto ei ole sallittu
Feb 17 19:28:52 serveri pulseaudio[6761]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 8000 Hz.
Feb 17 19:28:52 serveri pulseaudio[6761]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Feb 17 19:28:52 serveri pulseaudio[6761]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 8000 Hz.
Feb 17 19:28:52 serveri pulseaudio[6761]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Feb 17 19:29:09 serveri kernel: [  336.090045] khubd         D ffffffff80234069     0  1310      2
Feb 17 19:29:09 serveri kernel: [  336.090050]  ffff880037893760 0000000000000046 0000000000000000 ffff88003cf950c0
Feb 17 19:29:09 serveri kernel: [  336.090054]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090058]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090062] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.090102]  [<ffffffff80501ef5>] __mutex_lock_slowpath+0x85/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090109]  [<ffffffff80501c79>] ? mutex_unlock+0x9/0x20
Feb 17 19:29:09 serveri kernel: [  336.090114]  [<ffffffff80501c63>] mutex_lock+0x13/0x20
Feb 17 19:29:09 serveri kernel: [  336.090126]  [<ffffffffa0273a61>] i2c_add_adapter+0x41/0xc0 [i2c_core]
Feb 17 19:29:09 serveri kernel: [  336.090137]  [<ffffffffa0496f88>] dvb_usb_i2c_init+0x98/0xe0 [dvb_usb]
Feb 17 19:29:09 serveri kernel: [  336.090145]  [<ffffffffa04968a2>] dvb_usb_init+0x92/0x110 [dvb_usb]
Feb 17 19:29:09 serveri kernel: [  336.090152]  [<ffffffffa0496b1e>] dvb_usb_device_init+0x1fe/0x2e0 [dvb_usb]
Feb 17 19:29:09 serveri kernel: [  336.090164]  [<ffffffffa04b6025>] dibusb_mc_probe+0x25/0x28 [dvb_usb_dibusb_mc]
Feb 17 19:29:09 serveri kernel: [  336.090191]  [<ffffffffa013878c>] usb_probe_interface+0xcc/0x180 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090205]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:29:09 serveri kernel: [  336.090210]  [<ffffffff80431002>] really_probe+0x72/0x1a0
Feb 17 19:29:09 serveri kernel: [  336.090213]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:29:09 serveri kernel: [  336.090218]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:29:09 serveri kernel: [  336.090222]  [<ffffffff80431180>] driver_probe_device+0x50/0x60
Feb 17 19:29:09 serveri kernel: [  336.090225]  [<ffffffff8043122e>] __device_attach+0xe/0x10
Feb 17 19:29:09 serveri kernel: [  336.090229]  [<ffffffff804303cb>] bus_for_each_drv+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.090232]  [<ffffffff804312f8>] device_attach+0x88/0x90
Feb 17 19:29:09 serveri kernel: [  336.090237]  [<ffffffff804301b5>] bus_attach_device+0x55/0x80
Feb 17 19:29:09 serveri kernel: [  336.090240]  [<ffffffff8042eb9a>] device_add+0x3da/0x4b0
Feb 17 19:29:09 serveri kernel: [  336.090245]  [<ffffffff80234069>] ? __phys_addr+0x9/0x50
Feb 17 19:29:09 serveri kernel: [  336.090261]  [<ffffffffa0137378>] usb_set_configuration+0x4a8/0x640 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090265]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:29:09 serveri kernel: [  336.090283]  [<ffffffffa014060b>] generic_probe+0x3b/0xb0 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090289]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:29:09 serveri kernel: [  336.090304]  [<ffffffffa0137742>] usb_probe_device+0x42/0x50 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090308]  [<ffffffff80431002>] really_probe+0x72/0x1a0
Feb 17 19:29:09 serveri kernel: [  336.090314]  [<ffffffff80431220>] ? __device_attach+0x0/0x10
Feb 17 19:29:09 serveri kernel: [  336.090317]  [<ffffffff80431180>] driver_probe_device+0x50/0x60
Feb 17 19:29:09 serveri kernel: [  336.090321]  [<ffffffff8043122e>] __device_attach+0xe/0x10
Feb 17 19:29:09 serveri kernel: [  336.090324]  [<ffffffff804303cb>] bus_for_each_drv+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.090327]  [<ffffffff804312f8>] device_attach+0x88/0x90
Feb 17 19:29:09 serveri kernel: [  336.090332]  [<ffffffff804301b5>] bus_attach_device+0x55/0x80
Feb 17 19:29:09 serveri kernel: [  336.090335]  [<ffffffff8042eb9a>] device_add+0x3da/0x4b0
Feb 17 19:29:09 serveri kernel: [  336.090351]  [<ffffffffa0137ff0>] ? usb_autopm_do_device+0xc0/0x110 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090367]  [<ffffffffa0130c4f>] usb_new_device+0x6f/0xd0 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090383]  [<ffffffffa0131730>] hub_port_connect_change+0x510/0xad0 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090399]  [<ffffffffa013527a>] ? usb_free_urb+0x1a/0x20 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090402]  [<ffffffff80234069>] ? __phys_addr+0x9/0x50
Feb 17 19:29:09 serveri kernel: [  336.090418]  [<ffffffffa0136554>] ? usb_control_msg+0xf4/0x110 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090434]  [<ffffffffa0132103>] hub_events+0x2e3/0x650 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090450]  [<ffffffffa01324b5>] hub_thread+0x45/0x190 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090455]  [<ffffffff80266fd0>] ? autoremove_wake_function+0x0/0x40
Feb 17 19:29:09 serveri kernel: [  336.090471]  [<ffffffffa0132470>] ? hub_thread+0x0/0x190 [usbcore]
Feb 17 19:29:09 serveri kernel: [  336.090474]  [<ffffffff80266b9e>] kthread+0x4e/0x90
Feb 17 19:29:09 serveri kernel: [  336.090477]  [<ffffffff80213c99>] child_rip+0xa/0x11
Feb 17 19:29:09 serveri kernel: [  336.090480]  [<ffffffff80266b50>] ? kthread+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.090483]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
Feb 17 19:29:09 serveri kernel: [  336.090485] 
Feb 17 19:29:09 serveri kernel: [  336.090493] modprobe      D ffffffff80234069     0  2905      1
Feb 17 19:29:09 serveri kernel: [  336.090496]  ffff88003bd55ca8 0000000000000082 ffff88003e042808 ffff880001017470
Feb 17 19:29:09 serveri kernel: [  336.090500]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090504]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090507] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.090513]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090518]  [<ffffffff802473fe>] ? try_to_wake_up+0x11e/0x2e0
Feb 17 19:29:09 serveri kernel: [  336.090522]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090527]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.090531]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.090534]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.090537]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.090542]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090549]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:29:09 serveri kernel: [  336.090554]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.090557]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.090564]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:29:09 serveri kernel: [  336.090571]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.090578]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:29:09 serveri kernel: [  336.090585]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090591]  [<ffffffffa01a6000>] ? flexcop_pci_module_init+0x0/0x25 [b2c2_flexcop_pci]
Feb 17 19:29:09 serveri kernel: [  336.090597]  [<ffffffffa01a6023>] flexcop_pci_module_init+0x23/0x25 [b2c2_flexcop_pci]
Feb 17 19:29:09 serveri kernel: [  336.090601]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.090605]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.090613]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.090618]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.090620] 
Feb 17 19:29:09 serveri kernel: [  336.090626] modprobe      D ffffffff80234069     0  2911      1
Feb 17 19:29:09 serveri kernel: [  336.090630]  ffff88003bc61ca8 0000000000000082 ffffffff803a7b99 ffff880001017470
Feb 17 19:29:09 serveri kernel: [  336.090633]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090637]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090640] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.090645]  [<ffffffff803a7b99>] ? rb_insert_color+0x109/0x140
Feb 17 19:29:09 serveri kernel: [  336.090651]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090655]  [<ffffffff802473fe>] ? try_to_wake_up+0x11e/0x2e0
Feb 17 19:29:09 serveri kernel: [  336.090658]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090663]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.090666]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.090669]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.090673]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.090676]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090687]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:29:09 serveri kernel: [  336.090692]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.090695]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.090704]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:29:09 serveri kernel: [  336.090710]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.090719]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:29:09 serveri kernel: [  336.090724]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090733]  [<ffffffffa03237e0>] ? cx8800_init+0x0/0x40 [cx8800]
Feb 17 19:29:09 serveri kernel: [  336.090740]  [<ffffffffa032381a>] cx8800_init+0x3a/0x40 [cx8800]
Feb 17 19:29:09 serveri kernel: [  336.090743]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.090747]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.090754]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.090758]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.090760] 
Feb 17 19:29:09 serveri kernel: [  336.090766] modprobe      D ffffffff80234069     0  2913      1
Feb 17 19:29:09 serveri kernel: [  336.090769]  ffff88003bd35ca8 0000000000000086 ffff88003e4e80a0 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.090773]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090777]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090780] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.090785]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090789]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.090793]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090797]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.090801]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.090804]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.090807]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.090811]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090818]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:29:09 serveri kernel: [  336.090823]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.090826]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.090833]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:29:09 serveri kernel: [  336.090839]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.090846]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:29:09 serveri kernel: [  336.090851]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090858]  [<ffffffffa0455cd0>] ? cx88_audio_init+0x0/0x3c [cx88_alsa]
Feb 17 19:29:09 serveri kernel: [  336.090863]  [<ffffffffa0455d0a>] cx88_audio_init+0x3a/0x3c [cx88_alsa]
Feb 17 19:29:09 serveri kernel: [  336.090866]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.090870]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.090878]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.090881]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.090883] 
Feb 17 19:29:09 serveri kernel: [  336.090889] modprobe      D ffffffff80234069     0  2915      1
Feb 17 19:29:09 serveri kernel: [  336.090893]  ffff88003e0c9ca8 0000000000000082 ffff88003e0973c0 ffff880001017470
Feb 17 19:29:09 serveri kernel: [  336.090896]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090900]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.090903] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.090908]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090912]  [<ffffffff802473fe>] ? try_to_wake_up+0x11e/0x2e0
Feb 17 19:29:09 serveri kernel: [  336.090915]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090920]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.090924]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.090927]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.090930]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.090933]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.090941]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:29:09 serveri kernel: [  336.090946]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.090949]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.090957]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:29:09 serveri kernel: [  336.090963]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.090970]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:29:09 serveri kernel: [  336.090976]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.090983]  [<ffffffffa032e480>] ? cx8802_init+0x0/0x40 [cx8802]
Feb 17 19:29:09 serveri kernel: [  336.090989]  [<ffffffffa032e4ba>] cx8802_init+0x3a/0x40 [cx8802]
Feb 17 19:29:09 serveri kernel: [  336.090992]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.090996]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091003]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091007]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.091009] 
Feb 17 19:29:09 serveri kernel: [  336.091016] modprobe      D ffffffff80234069     0  3017      1
Feb 17 19:29:09 serveri kernel: [  336.091019]  ffff88003e003c68 0000000000000082 ffff8800378635f0 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.091022]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091026]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091029] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.091034]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091038]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.091041]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091046]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.091049]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.091053]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.091056]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.091059]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091064]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.091068]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.091075]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.091083]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091092]  [<ffffffffa01ae3a1>] parport_pc_find_ports+0xda/0x114 [parport_pc]
Feb 17 19:29:09 serveri kernel: [  336.091100]  [<ffffffffa01ae481>] parport_pc_init+0xa6/0xab [parport_pc]
Feb 17 19:29:09 serveri kernel: [  336.091108]  [<ffffffffa01ae3db>] ? parport_pc_init+0x0/0xab [parport_pc]
Feb 17 19:29:09 serveri kernel: [  336.091111]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.091114]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091122]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091126]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.091128] 
Feb 17 19:29:09 serveri kernel: [  336.091134] modprobe      D ffffffff80234069     0  3293      1
Feb 17 19:29:09 serveri kernel: [  336.091137]  ffff88003bd77ca8 0000000000000086 ffff88003e47bd70 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.091141]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091144]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091148] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.091153]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091156]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.091160]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091164]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.091168]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.091171]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.091174]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.091178]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091183]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:29:09 serveri kernel: [  336.091188]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.091191]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.091198]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:29:09 serveri kernel: [  336.091204]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.091210]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:29:09 serveri kernel: [  336.091215]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091221]  [<ffffffffa01b6000>] ? i2c_vt596_init+0x0/0x25 [i2c_viapro]
Feb 17 19:29:09 serveri kernel: [  336.091226]  [<ffffffffa01b6023>] i2c_vt596_init+0x23/0x25 [i2c_viapro]
Feb 17 19:29:09 serveri kernel: [  336.091229]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.091233]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091240]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091244]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.091246] 
Feb 17 19:29:09 serveri kernel: [  336.091253] modprobe      D ffffffff80234069     0  3307      1
Feb 17 19:29:09 serveri kernel: [  336.091256]  ffff88003e477ca8 0000000000000082 ffff88003e957780 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.091259]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091263]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091266] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.091271]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091275]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.091278]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091283]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.091286]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.091290]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.091293]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.091296]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091303]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:29:09 serveri kernel: [  336.091308]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.091312]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.091318]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:29:09 serveri kernel: [  336.091325]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.091331]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:29:09 serveri kernel: [  336.091337]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091343]  [<ffffffffa04ee000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx_modem]
Feb 17 19:29:09 serveri kernel: [  336.091348]  [<ffffffffa04ee023>] alsa_card_via82xx_init+0x23/0x25 [snd_via82xx_modem]
Feb 17 19:29:09 serveri kernel: [  336.091351]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.091355]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091363]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091366]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.091368] 
Feb 17 19:29:09 serveri kernel: [  336.091375] modprobe      D ffffffff80234069     0  3337      1
Feb 17 19:29:09 serveri kernel: [  336.091378]  ffff88003dd6dca8 0000000000000082 ffff88003cca5550 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.091381]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091385]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091388] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.091393]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091397]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.091400]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091405]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.091408]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.091412]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.091415]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.091418]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091424]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:29:09 serveri kernel: [  336.091429]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.091432]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.091438]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:29:09 serveri kernel: [  336.091444]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.091450]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:29:09 serveri kernel: [  336.091455]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091460]  [<ffffffffa0509000>] ? k8temp_init+0x0/0x25 [k8temp]
Feb 17 19:29:09 serveri kernel: [  336.091465]  [<ffffffffa0509023>] k8temp_init+0x23/0x25 [k8temp]
Feb 17 19:29:09 serveri kernel: [  336.091468]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.091471]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091479]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091483]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.091485] 
Feb 17 19:29:09 serveri kernel: [  336.091491] modprobe      D ffffffff80234069     0  3343   3342
Feb 17 19:29:09 serveri kernel: [  336.091494]  ffff88003ccb3ca8 0000000000000086 ffff88003dccfe10 0000000000000000
Feb 17 19:29:09 serveri kernel: [  336.091498]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091502]  ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400
Feb 17 19:29:09 serveri kernel: [  336.091505] Call Trace:
Feb 17 19:29:09 serveri kernel: [  336.091510]  [<ffffffff80501975>] schedule_timeout+0x95/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091514]  [<ffffffff803a4a68>] ? kobject_add_varg+0x38/0x60
Feb 17 19:29:09 serveri kernel: [  336.091517]  [<ffffffff80502386>] __down+0x76/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091522]  [<ffffffff8026bd3c>] down+0x4c/0x50
Feb 17 19:29:09 serveri kernel: [  336.091525]  [<ffffffff804311c7>] __driver_attach+0x37/0x90
Feb 17 19:29:09 serveri kernel: [  336.091529]  [<ffffffff80431190>] ? __driver_attach+0x0/0x90
Feb 17 19:29:09 serveri kernel: [  336.091532]  [<ffffffff8043078b>] bus_for_each_dev+0x6b/0xa0
Feb 17 19:29:09 serveri kernel: [  336.091535]  [<ffffffff802e1f9b>] ? kmem_cache_alloc+0x8b/0xd0
Feb 17 19:29:09 serveri kernel: [  336.091544]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091549]  [<ffffffff80430e61>] driver_attach+0x21/0x30
Feb 17 19:29:09 serveri kernel: [  336.091552]  [<ffffffff8042fff8>] bus_add_driver+0x1f8/0x270
Feb 17 19:29:09 serveri kernel: [  336.091559]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091565]  [<ffffffff80431415>] driver_register+0x75/0x170
Feb 17 19:29:09 serveri kernel: [  336.091572]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091578]  [<ffffffff803bcaf2>] __pci_register_driver+0x72/0xc0
Feb 17 19:29:09 serveri kernel: [  336.091585]  [<ffffffffa0502000>] ? alsa_card_via82xx_init+0x0/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091590]  [<ffffffffa0502023>] alsa_card_via82xx_init+0x23/0x25 [snd_via82xx]
Feb 17 19:29:09 serveri kernel: [  336.091593]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
Feb 17 19:29:09 serveri kernel: [  336.091597]  [<ffffffff8026c1c1>] ? __blocking_notifier_call_chain+0x21/0x90
Feb 17 19:29:09 serveri kernel: [  336.091605]  [<ffffffff8027cfd5>] sys_init_module+0xb5/0x1f0
Feb 17 19:29:09 serveri kernel: [  336.091608]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Feb 17 19:29:09 serveri kernel: [  336.091610] 
F

---

### Post by Mr.Carramba on 2009-02-18
I think that is very related to your kernel upgrade.
enter grub menu and boot with old one.
if this is solving your problem, then maybe waite for the next kernel upgrade?

---

### Post by tlindvall on 2009-02-19
I did some boot tests with earlier kernel.  It works just the same way.  I also changed to text console mode during the boot and noted the messages before the hang.  It hangs here for about two minutes.  My current hypothesis is that previous time out messages are caused by that hang and the root cause is the hang.  As you can see last error messages before hang are from flexcop driver (technisat airstar 2 card).  I assume the problematic driver is one of the drivers between this and the event when kernel recognizes hang (modprobe blocked for more than 120 seconds), so suspected devices/drivers are:
flexcop driver (technisat airstar 2)
parport_pc (parallel port driver)
bttv driver (Bt878)
cx2388x alsa driver
USB Bidirectional printer driver
yealink: Yealink phone driver
Artec T14 - USB2.0 DVB-T driver
PC Speaker
ImPS/2 Generic Wheel Mouse

I will continue by removing bt878, because it is the only one not identified by the kernel.

regs

************************************************************************

tail /var/log/dmesg

...
[   35.782077] flexcop-pci: will use the HW PID filter.
[   35.782081] flexcop-pci: card revision 2
[   35.782090] b2c2_flexcop_pci 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   35.820152] DVB: registering new adapter (FlexCop Digital TV device)
[   35.821920] b2c2-flexcop: MAC address = 00:d0:d7:0b:7a:67
[   35.822184] b2c2-flexcop: i2c master_xfer failed
[   35.822550] b2c2-flexcop: i2c master_xfer failed
[   35.822609] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[   35.822670] CX24123: wrong demod revision: 87
[   35.855182] b2c2-flexcop: i2c master_xfer failed
[   35.957540] parport_pc 00:07: reported by Plug and Play ACPI
[   35.957584] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   36.060432] b2c2-flexcop: i2c master_xfer failed       *** This is the last message in the console before hang
[   36.141893] b2c2-flexcop: found 'Zarlink MT352 DVB-T' .
[   36.141898] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   36.142051] b2c2-flexcop: initialization of 'Air2PC/AirStar 2 DVB-T' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
[   36.144220] bttv: Bt8xx card found (0).
[   36.144241] bttv 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   36.144253] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 18, latency: 64, mmio: 0xeef00000
[   36.144268] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   36.144321] bttv0: gpio: en=00000000, out=00000000 in=00f360ff [init]
[   36.203537] cx2388x alsa driver version 0.0.6 loaded
[   38.052165] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04E8 pid 0x3413
[   38.062984] usblp1: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB802
[   38.063016] usbcore: registered new interface driver usblp
[   38.575391] input: Yealink usb-p1k as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.3/input/input6
[   38.615885] usbcore: registered new interface driver snd-usb-audio
[   38.616488] usbcore: registered new interface driver yealink
[   38.616492] yealink: Yealink phone driver:yld-20051230
[   39.000727] dvb-usb: found a 'Artec T14 - USB2.0 DVB-T' in warm state.
[   39.035210] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   39.800100] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[  199.720009] INFO: task modprobe:2939 blocked for more than 120 seconds.
...

---

### Post by tlindvall on 2009-02-19
I disabled quit mode and getting more exact info:

[   98.910468] cx8800 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   98.911450] cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]
[   98.911526] cx88[0]: TV tuner type 63, Radio tuner type -1
**hanging here***
[  214.339483] loop: module loaded
[  214.386382] lp0: using parport0 (interrupt-driven).

I assume the problematic driver is cx88?  I have an old fedora system on a different disk and the same hardware works just fine (I was planning to move to ubuntu), so looks like this is ubuntu 8.10 related problem.  I am not having very good linux skills, so any advice would  be appreciated.

Regs Tarmo

---

### Post by tlindvall on 2009-02-19
Actually the problematic driver was bttv driver.  The boot hanging was solved by adding couple of lines to modprobe.conf.  These might help someone else encountering same problems so here they are:
options i2c-algo-bit bit_test=1
options bttv card=77 tuner=4 radio=0 triton1=0 vsfx=0 autoload=0

regs Tarmo

:D

---

