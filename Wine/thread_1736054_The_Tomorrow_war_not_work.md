---
title: "The Tomorrow war not work"
date: 2011-04-22
forum: Wine
---

### Post by smart734 on 2011-04-22
Hello, i have tomorrow war game. Install and play work, but if i fly into war, game stop with window Program error. I console:

```
martin@kluci:~/.wine/drive_c/Program Files/1C Company/The Tomorrow War$ wine zv.exe 
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32d590,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cfb4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d0a4,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a760-90c8-11d0-bd43-00a0c911ce86} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:win:EnumDisplayDevicesW ((null),0,0x32e070,0x00000000), stub!
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:win:EnumDisplayDevicesW ((null),0,0x32df4c,0x00000000), stub!
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7d26aaa0 stub tag
fixme:gstreamer:event_sink 0x7d26a990 stub tag
fixme:gstreamer:event_sink 0x7d26aa28 stub tag
fixme:gstreamer:event_sink 0x7d26a990 stub tag
fixme:gstreamer:got_data_sink Triggering 0x7de04588 0xbc
fixme:gstreamer:got_data_sink Triggering 0x7de044c0 0xc0
fixme:gstreamer:watch_bus avidemux0: Vnit&#345;ní chyba datového proudu.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x18fe00,0x190700): stub
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a86897-0ad4-11ce-b03a-0020af0ba770}!
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7d29d8f0 stub tag
fixme:gstreamer:event_sink 0x7d29d940 stub tag
fixme:gstreamer:event_sink 0x7d29d918 stub tag
fixme:gstreamer:event_sink 0x7d29d940 stub tag
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:quartz:DSoundRender_SendSampleData Sample dropped 13420 of 88200 bytes
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:gstreamer:got_data_sink Did not get a GST_APP_BUFFER, creating a sample
fixme:quartz:DSoundRender_UpdatePositions Underrun of data occurred!
fixme:gstreamer:Gstreamer_transform_Cleanup 0x18e478 stub
fixme:gstreamer:Gstreamer_transform_Cleanup 0x18e478 stub
fixme:gstreamer:Gstreamer_transform_Cleanup 0x18e478 stub
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:init_new_decoded_pad Linking: 0
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7d3421b8 stub tag
fixme:gstreamer:event_sink 0x7d342000 stub tag
fixme:gstreamer:event_sink 0x7d341fb8 stub tag
fixme:gstreamer:event_sink 0x7d342000 stub tag
fixme:gstreamer:event_sink 0x7d29db18 stub tag
fixme:gstreamer:event_sink 0x7d29d990 stub tag
fixme:gstreamer:got_data_sink Triggering 0x7d29d718 0xbc
fixme:gstreamer:got_data_sink Triggering 0x7d29d650 0xb4
fixme:gstreamer:watch_bus avidemux2: Vnit&#345;ní chyba datového proudu.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x190418,0x190da8): stub
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a86897-0ad4-11ce-b03a-0020af0ba770}!
fixme:gstreamer:no_more_pads Done
fixme:gstreamer:event_sink 0x7dcc6918 stub tag
fixme:gstreamer:event_sink 0x7dcc6940 stub tag
fixme:gstreamer:event_sink 0x7dcc68f0 stub tag
fixme:gstreamer:event_sink 0x7dcc6940 stub tag
fixme:gstreamer:event_sink 0x7d341cf0 stub tag
fixme:gstreamer:event_sink 0x7d341cc8 stub tag
fixme:quartz:DSoundRender_SendSampleData Sample dropped 13416 of 4608 bytes
fixme:quartz:DSoundRender_SendSampleData Sample dropped 8808 of 4608 bytes
fixme:quartz:DSoundRender_SendSampleData Sample dropped 4200 of 4608 bytes
fixme:quartz:DSoundRender_UpdatePositions Underrun of data occurred!
fixme:gstreamer:Gstreamer_transform_Cleanup 0x18d838 stub
fixme:gstreamer:Gstreamer_transform_Cleanup 0x18d838 stub
fixme:gstreamer:Gstreamer_transform_Cleanup 0x18d838 stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32da24,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x190368,0x1900b0): stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:dinput:SysMouseWImpl_Acquire Clipping cursor to (0,0)-(1024,768)
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x2cb4998,1,0x32d550,0x32d59c): stub
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x2cc2e70,1,0x32d550,0x32d59c): stub
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x2b1ca50,1,0x32d554,0x32d5a0): stub
fixme:dsound:IDirectSoundBufferImpl_SetFX (0xa390e68,1,0x32d18c,0x32d1d8): stub
fixme:dsound:IDirectSoundBufferImpl_SetFX (0xa117138,1,0x32d18c,0x32d1d8): stub
fixme:d3d:wined3d_buffer_preload Too many full buffer conversions, stopping converting.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #146:
fixme:d3d_shader:print_glsl_info_log     Vertex info
fixme:d3d_shader:print_glsl_info_log     -----------
fixme:d3d_shader:print_glsl_info_log     0(10) : warning C7050: "R2.w" might be used before being initialized
wine: Unhandled page fault on read access to 0x00000000 at address 0x67a36e (thread 0009), starting debugger...
```

I dont know, what i must do to play. I try to found this problem on google but nothing and on winehq.com there isnt this game. P.S. Sorry fo my english.

Thanks for help.

---

