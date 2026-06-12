---
title: "php-libvirt-php missing functions?"
date: 2016-06-12
forum: Virtualisation
---

### Post by philled on 2016-06-12
I'm trying to write some PHP scripts using php-libvirt-php. I've been basing it on a script I saw online but I'm getting errors about undefined functions, eg:

[FONT=courier new]Fatal error: Uncaught Error: [COLOR=#ff0000]**Call to undefined function libvirt_get_hostname()**[/COLOR] in /var/www/html/libvirt_test1.php:19 Stack trace: #0 {main} thrown in /var/www/html/libvirt_test1.php on line 19[/FONT]

But libvirt_get_hostname() is supposed to be part of php-libvirt-php, isn't it? The list of functions is at [http://phplibvirt.cybersales.cz/doc/book.libvirt.html](http://phplibvirt.cybersales.cz/doc/book.libvirt.html) 

So is there something wrong with the package I've installed, or am I misunderstanding something here?

---

### Post by MAFoElffen on 2016-06-16
If not seeing a basic function of php-libvirt ... I am assuming that it is compiled and installed, right? 

When done so, that creates modules/libvirt.so which you either copy to your modules directory --OR-- In your php.ini file, you add a line that says:
```
 
extension=libvirt.so

```
...which in other languages would be like saying import, link or using that module. Those 2 methods are how it finds that module.

Taking that in mind, did you do either for it to find php-libvirt.so in it's path? The thing to do would be to check your php.ini file to look for that line and to check your modules directory for the file "libvirt.so".

---

### Post by philled on 2016-06-16
> **MAFoElffen said:**
> If not seeing a basic function of php-libvirt ... I am assuming that it is compiled and installed, right? 
When done so, that creates modules/libvirt.so which you either copy to your modules directory --OR-- In your php.ini file, you add a line that says:
```
 
extension=libvirt.so

```
...which in other languages would be like saying import, link or using that module. Those 2 methods are how it finds that module.
Taking that in mind, did you do either for it to find php-libvirt.so in it's path? The thing to do would be to check your php.ini file to look for that line and to check your modules directory for the file "libvirt.so".

I haven't compiled anything - I installed the package php-libvirt-php. So all the modules should be available from that shouldn't they? That being the case. do I still need to add the extension line to php.ini?

---

### Post by MAFoElffen on 2016-06-16
You want to see if that module loads>
```

<?php
print_r(get_extension_funcs("libvirt"));
?>

```
If a module is loaded, print out a list of all the functions of...

---

### Post by philled on 2016-06-18
> **MAFoElffen said:**
> You want to see if that module loads>
```

<?php
print_r(get_extension_funcs("libvirt"));
?>

```
If a module is loaded, print out a list of all the functions of...

Below is what it prints (after a bit of manual formatting with new lines). Perhaps the problem is that the example I copied from called libvirt_get_hostname but should have called libvirt_[COLOR=#ff0000]connect[/COLOR]_get_hostname
```

[FONT=courier new]Array (
[0] => libvirt_get_last_error
[1] => libvirt_connect
[2] => libvirt_connect_get_uri
[3] => libvirt_connect_get_hostname
[4] => libvirt_connect_get_capabilities
[5] => libvirt_connect_get_emulator
[6] => libvirt_connect_get_nic_models
[7] => libvirt_connect_get_soundhw_models
[8] => libvirt_connect_get_information
[9] => libvirt_connect_get_machine_types
[10] => libvirt_connect_get_hypervisor
[11] => libvirt_connect_get_sysinfo
[12] => libvirt_connect_get_maxvcpus
[13] => libvirt_connect_get_encrypted
[14] => libvirt_connect_get_secure
[15] => libvirt_connect_get_all_domain_stats
[16] => libvirt_stream_create
[17] => libvirt_stream_close
[18] => libvirt_stream_abort
[19] => libvirt_stream_finish
[20] => libvirt_stream_send
[21] => libvirt_stream_recv
[22] => libvirt_domain_new
[23] => libvirt_domain_new_get_vnc
[24] => libvirt_domain_get_counts
[25] => libvirt_domain_is_persistent
[26] => libvirt_domain_lookup_by_name
[27] => libvirt_domain_get_xml_desc
[28] => libvirt_domain_get_disk_devices
[29] => libvirt_domain_get_interface_devices
[30] => libvirt_domain_change_vcpus
[31] => libvirt_domain_change_memory
[32] => libvirt_domain_change_boot_devices
[33] => libvirt_domain_disk_add
[34] => libvirt_domain_disk_remove
[35] => libvirt_domain_nic_add
[36] => libvirt_domain_nic_remove
[37] => libvirt_domain_get_info
[38] => libvirt_domain_get_name
[39] => libvirt_domain_get_uuid
[40] => libvirt_domain_get_uuid_string
[41] => libvirt_domain_get_id
[42] => libvirt_domain_lookup_by_id
[43] => libvirt_domain_lookup_by_uuid
[44] => libvirt_domain_lookup_by_uuid_string
[45] => libvirt_domain_destroy
[46] => libvirt_domain_create
[47] => libvirt_domain_resume
[48] => libvirt_domain_core_dump
[49] => libvirt_domain_shutdown
[50] => libvirt_domain_suspend
[51] => libvirt_domain_managedsave
[52] => libvirt_domain_undefine
[53] => libvirt_domain_reboot
[54] => libvirt_domain_define_xml
[55] => libvirt_domain_create_xml
[56] => libvirt_domain_memory_peek
[57] => libvirt_domain_memory_stats
[58] => libvirt_domain_set_memory
[59] => libvirt_domain_set_max_memory
[60] => libvirt_domain_set_memory_flags
[61] => libvirt_domain_block_commit
[62] => libvirt_domain_block_stats
[63] => libvirt_domain_block_resize
[64] => libvirt_domain_block_job_abort
[65] => libvirt_domain_block_job_set_speed
[66] => libvirt_domain_block_job_info
[67] => libvirt_domain_interface_stats
[68] => libvirt_domain_get_connect
[69] => libvirt_domain_migrate
[70] => libvirt_domain_migrate_to_uri
[71] => libvirt_domain_migrate_to_uri2
[72] => libvirt_domain_get_job_info
[73] => libvirt_domain_xml_xpath
[74] => libvirt_domain_get_block_info
[75] => libvirt_domain_get_network_info
[76] => libvirt_domain_get_autostart
[77] => libvirt_domain_set_autostart
[78] => libvirt_domain_get_metadata
[79] => libvirt_domain_set_metadata
[80] => libvirt_domain_is_active
[81] => libvirt_domain_get_next_dev_ids
[82] => libvirt_domain_get_screenshot
[83] => libvirt_domain_get_screenshot_api
[84] => libvirt_domain_get_screen_dimensions
[85] => libvirt_domain_send_keys
[86] => libvirt_domain_send_pointer_event
[87] => libvirt_domain_update_device
[88] => libvirt_domain_has_current_snapshot
[89] => libvirt_domain_snapshot_create
[90] => libvirt_domain_snapshot_get_xml
[91] => libvirt_domain_snapshot_revert
[92] => libvirt_domain_snapshot_delete
[93] => libvirt_domain_snapshot_lookup_by_name
[94] => libvirt_storagepool_lookup_by_name
[95] => libvirt_storagepool_lookup_by_volume
[96] => libvirt_storagepool_get_info
[97] => libvirt_storagevolume_lookup_by_name
[98] => libvirt_storagevolume_lookup_by_path
[99] => libvirt_storagevolume_get_name
[100] => libvirt_storagevolume_get_path
[101] => libvirt_storagevolume_get_info
[102] => libvirt_storagevolume_get_xml_desc
[103] => libvirt_storagevolume_create_xml
[104] => libvirt_storagevolume_create_xml_from
[105] => libvirt_storagevolume_delete
[106] => libvirt_storagevolume_download
[107] => libvirt_storagevolume_upload
[108] => libvirt_storagevolume_resize
[109] => libvirt_storagepool_get_uuid_string
[110] => libvirt_storagepool_get_name
[111] => libvirt_storagepool_lookup_by_uuid_string
[112] => libvirt_storagepool_get_xml_desc
[113] => libvirt_storagepool_define_xml
[114] => libvirt_storagepool_undefine
[115] => libvirt_storagepool_create
[116] => libvirt_storagepool_destroy
[117] => libvirt_storagepool_is_active
[118] => libvirt_storagepool_get_volume_count
[119] => libvirt_storagepool_refresh
[120] => libvirt_storagepool_set_autostart
[121] => libvirt_storagepool_get_autostart
[122] => libvirt_storagepool_build
[123] => libvirt_storagepool_delete
[124] => libvirt_network_define_xml
[125] => libvirt_network_undefine
[126] => libvirt_network_get
[127] => libvirt_network_get_xml_desc
[128] => libvirt_network_get_bridge
[129] => libvirt_network_get_information
[130] => libvirt_network_get_active
[131] => libvirt_network_set_active
[132] => libvirt_node_get_info
[133] => libvirt_node_get_cpu_stats
[134] => libvirt_node_get_cpu_stats_for_each_cpu
[135] => libvirt_node_get_mem_stats
[136] => libvirt_nodedev_get
[137] => libvirt_nodedev_capabilities
[138] => libvirt_nodedev_get_xml_desc
[139] => libvirt_nodedev_get_information
[140] => libvirt_list_domains
[141] => libvirt_list_domain_snapshots
[142] => libvirt_list_domain_resources
[143] => libvirt_list_nodedevs
[144] => libvirt_list_networks
[145] => libvirt_list_storagepools
[146] => libvirt_list_active_storagepools
[147] => libvirt_list_inactive_storagepools
[148] => libvirt_storagepool_list_volumes
[149] => libvirt_list_active_domains
[150] => libvirt_list_active_domain_ids
[151] => libvirt_list_inactive_domains
[152] => libvirt_version
[153] => libvirt_check_version
[154] => libvirt_has_feature
[155] => libvirt_get_iso_images
[156] => libvirt_image_create
[157] => libvirt_image_remove
[158] => libvirt_logfile_set
[159] => libvirt_print_binding_resources
[160] => libvirt_domain_qemu_agent_command )

```[/FONT]

---

### Post by MAFoElffen on 2016-06-18
Yes. I see that. Maybe a difference in the package flavor of that library or version of that library. I could have sworn when I just looked it up in the doc's a few days ago, that that specific function was as you stated. But the output shows differently.

I just got bit on something else, where I explained how to do something using a package that isn't available anymore. Boy did I feel foolish. Things do change.

---

### Post by MAFoElffen on 2016-06-19
So did you change your code to that function and get the results your were looking for?

If so, then you can mark this as solved. I think you got your answer "why" you got the error, but I'm thinking you want to get your script working, right?

---

