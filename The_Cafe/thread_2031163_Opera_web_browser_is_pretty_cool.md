---
title: "Opera web browser is pretty cool"
date: 2012-07-21
forum: The Cafe
---

### Post by Welly Wu on 2012-07-21
Today I was having problems with both Google Chrome and Google Chromium. I could not play .WMV video files on certain websites. I also found the user interface to be quite spartan especially when it comes to managing dozens of open tabs.

I decided to download and install Opera web browser version 12.00. I have a System76 Lemur Ultra (lemu4) with Ubuntu 12.04 64 bit Long Term Service.

Opera is pretty darn innovative. I like the stackable tabbed browsing feature and I like the built-in e-mail and news features. I have an Opera account so I synchronized everything to it. I also downloaded and I installed the LastPass add-on since I have a LastPass Premium account.

It's very fast. I have Verizon FIOS fiber optic Internet [15 MB/s download and 5 MB/s upload] and I turned on Opera Turbo mode. I can load roughly 30 tabs in mere seconds on a cold launch.

Opera comes with almost all of the popular media plug-ins pre-installed. I can view most multimedia content on websites without having to do anything special. Opera is also efficient when it comes to energy consumption and memory usage. It's pretty lean and it consumes very little resources. I find that it consumes 1 less gigabyte of RAM and it gives me roughly 15 minutes of extra battery life compared to Google Chrome or Google Chromium.

There are not a lot of add-ons and widgets, but I think that the stock Opera web browser is pretty features rich. I like the instant notification pop-ups to tell me when I get an e-mail message. It's pretty unobtrusive.

I was looking for an alternative web browser and I think that I found Opera to be a suitable replacement. I have yet to try out the FTP server feature, but it could be quite useful for me in the future.

Overall, I think that Opera 12.00 offers numerous features and capabilities to cater to heavy web surfers. I checked several reputable vulnerability databases and Opera does not seem to get a lot of attention by attackers worldwide due to the fact that it has marginal market share. It seems to be a much safer alternative to Mozilla Firefox, Google Chrome, and Microsoft Windows Internet Explorer. I like the fact that it is available on numerous platforms and there are mobile versions available for Google Android 4.0.3 Ice Cream Sandwich. I have an ASUS EEE Pad Transformer TF101 tablet and I installed Opera Mobile.

I have no doubt that there are Opera fans here so I would like to know what kind of add-ons and widgets did you install and why? I would also like to know how to be able to turn on GPU hardware acceleration.

Thanks.

---

### Post by Welly Wu on 2012-07-21
I figured out how to turn on GPU hardware acceleration and WebGL in Opera 12. Now, it is much faster and it works. This is great.

---

### Post by Frogs Hair on 2012-07-21
I like Opera also . They have done away with Opera widgets now have quite a variety of extensions. Yes, there are some Opera fans and users among forum members. :o

---

### Post by PaulW2U on 2012-07-21
> **Frogs Hair said:**
>  Yes, there are some Opera fans and users among forum members. :o

Indeed.  I have it installed on my PC, my laptops, netbook and mobile phones. I've been using it since about 1998 when it wasn't free. You had to pay for it!

[History of the Opera web browser]("http://en.wikipedia.org/wiki/History_of_the_Opera_web_browser") shows how it went from trialware to adware and freeware.

---

### Post by bobsan on 2012-07-21
Opera is very slick, but I am having problems with it though. To list a few things, gecko-mediaplayer doesn't work in Opera for Ubuntu12.04, so many media contents don't play, webGL doesn't work with nouveau because hardware acceleration is disabled (works in Firefox and Chrome, just need to set a few options but there is no option in Opera)I haven't checked this with Opera 12 yet, but with Opera 11 I couldn't connect to localhost with LAMP, again no problem with Firefox and Chrome.

Opera is not going to have h264 support, so without flash and cannot play many html5 videos it will be a big problem, this is like Firefox now  but FF will support h264. 

I keep Opera only for testing. My main browser is Firefox, followed by Chrome.

---

### Post by Welly Wu on 2012-07-21
I think that you should download and install Opera 12 to see if it resolves your specific issues. Opera worked hard on bug fixes with their latest version which is currently version 12.00.

I am having no problem with GPU hardware acceleration and WebGL. It works. I don't really access websites with H264 codec and content so Opera 12.00 works for me.

---

### Post by bobsan on 2012-07-21
I have installed Opera 12. The only thing I haven't tested with it is accessing localhost. I see that hardware acceleration is turned off so no webgl(I can't find a way to override the default to turn it on like in Firefox or Chrome). The gecko-mediaplayer thing is a gecko-mediaplayer bug, it doesn't work in Chrome either for Ubuntu 12.04.

---

### Post by Welly Wu on 2012-07-21
[http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12](http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12)

Here is the official Opera blog to turn on GPU hardware acceleration and WebGL. You will need to set both options to 1 instead of 0 and restart Opera for the changes to take into effect.

---

### Post by bobsan on 2012-07-21
> **Welly Wu said:**
> [http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12](http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12)

Here is the official Opera blog to turn on GPU hardware acceleration and WebGL. You will need to set both options to 1 instead of 0 and restart Opera for the changes to take into effect.

Thanks, will try that later.

---

### Post by bobsan on 2012-07-21
> **Welly Wu said:**
> [http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12](http://my.opera.com/desktopteam/blog/2012/04/20/update-on-hardware-acceleration-in-opera-12)

Here is the official Opera blog to turn on GPU hardware acceleration and WebGL. You will need to set both options to 1 instead of 0 and restart Opera for the changes to take into effect.


It doesn't work. I just checked, I have actually already set those options to 1.

Here is what opera:gpu says

```
Hardware acceleration status
Hardware acceleration
Enabled 
Graphics backend
OpenGL 
OpenGL
Blocklist status
Blocklist version
1.0.5 
Blocklist status for 2D
Supported 
Blocklist status for 3D
Blocked driver version: Nouveau drivers crash when compiling some fragment shaders.
```

I cannot find a way to unblock Nouveau. In Chrome Noveau was blacklisted by default but it is easy to unblacklist it and I have had no problem with pages that require webGL (My driver is much more updated than Ubuntu's default as I installed it through ppa.)

---

### Post by Welly Wu on 2012-07-21
Hardware acceleration status
Hardware acceleration
Enabled 
Graphics backend
OpenGL 
OpenGL
Blocklist status
Blocklist version
1.0.5 
Blocklist status for 2D
Supported 
Blocklist status for 3D
Supported 
Graphics hardware and driver details
GL_VENDOR
Tungsten Graphics, Inc 
GL_RENDERER
Mesa DRI Intel(R) Ivybridge Mobile  
GL_VERSION
2.1 Mesa 8.0.2 
GL_EXTENSIONS
GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_framebuffer_sRGB GL_ARB_multitexture GL_EXT_framebuffer_sRGB GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_color_buffer_float GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_float GL_ARB_texture_rectangle GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_draw_buffers2 GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_integer GL_EXT_texture_sRGB_decode GL_EXT_timer_query GL_OES_EGL_image GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_depth_buffer_float GL_ARB_half_float_vertex GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_shader_texture_lod GL_EXT_provoking_vertex GL_EXT_texture_snorm GL_MESA_texture_signed_rgba GL_ARB_robustness  
GL_SHADING_LANGUAGE_VERSION
1.30 
Download driver

Mine seems to be working just fine. I purchased my System76 Lemur Ultra (lemu4) on June 26th, 2012 and I got it on July 5th, 2012.

I really don't know how to help you since I just switched to Opera 12.00 today.

---

### Post by bobsan on 2012-07-21
Don't worry about it. I only use Opera for testing. :)

---

### Post by Version Dependency on 2012-07-21
I always install Opera on my machines even though I use Firefox.  Sometimes I find sites that Firefox just doesn't play well with, but Opera does.

---

### Post by Welly Wu on 2012-07-21
Opera version 12.00 has really easy to read fonts and scrolling up and down web sites is very smooth and fluid. It is also the fastest web browser that I have tried on Ubuntu and Microsoft Windows. It is much faster than Google Chrome or Google Chromium especially with Opera Turbo turned on automatically. I have not had any problems with Opera version 12.00 other than I had to create a new ~/.opera folder in my /home directory by typing in sudo mv ~/.opera ~/.opera.bak to get it to launch properly. Other than that simple fix, Opera version 12.00 is by far my most favorite web browser.

I wish that there were more extensions. I wish that I could read my Amazon Kindle books using Opera. However, I have Codeweavers' CrossOver for Linux 64 bit version 11.2.0 and I have Microsoft Windows 7 64 bit Ultimate Edition Service Pack 1 using an Oracle VM Virtualbox guest virtual machine so I installed Amazon Kindle for PC. It works. I can still read my Amazon Kindle books on my System76 Lemur Ultra (lemu4).

Opera 12.00 is very slick. GPU hardware acceleration and WebGL made a huge difference in terms of speed and performance. Now, JavaScript, CSS3, HTML5, Adobe Flash, WebGL standards load up very fast on all web sites. It makes for a much richer and more interactive web browsing experience that is quite dynamic and fluid.

The built-in e-mail client and the chat features are very nice. I have yet to try the RSS reader feature and I will get around to it later. I still don't know where the FTP server feature is, but I will check out the [http://www.opera.com](http://www.opera.com) website for more information. I like being able to do my web surfing, chatting, e-mail and RSS reading in Opera version 12.00. I don't have to switch between specialized software applications within Ubuntu or Microsoft Windows 7 to handle these tasks anymore. It is true that I have 16.00 GB of PC3-12800 SDRAM, but Opera 12.00 is energy and memory efficient. I am more productive using Opera 12.00. I get more work done with fewer hassles and problems using Opera 12.00. It has streamlined my digital workflow quite nicely.

I have made Opera 12.00 my default web browser of choice in Ubuntu 12.04 64 bit Long Term Service. This is my daily driver.

---

### Post by BigSilly on 2012-07-21
Well I'll consider myself alone then. I found Opera to be quite a bit overrated by its fans, being more than a bit buggy in the interface department, and often hanging indefinitely when trying to access sites. I gave it a good go, but it's still very much Firefox for me.

---

### Post by JustinR on 2012-07-21
> **BigSilly said:**
> Well I'll consider myself alone then. I found Opera to be quite a bit overrated by its fans, being more than a bit buggy in the interface department, and often hanging indefinitely when trying to access sites. I gave it a good go, but it's still very much Firefox for me.

Very alone.

I like the fact that Opera has been a constant innovator in it's field, e.g. most recently Speed Dial and more things like that. It works great with 90+ tabs, and renders pages great.

---

### Post by Peripheral Visionary on 2012-07-22
> **BigSilly said:**
> Well I'll consider myself alone then. I found Opera to be quite a bit overrated by its fans, being more than a bit buggy in the interface department, and often hanging indefinitely when trying to access sites. I gave it a good go, but it's still very much Firefox for me.

Not alone at all. To be fair, though, my hardware is pretty old and low-spec. It runs Xubu 12.04 nicely though, and I find Seamonkey's built-in Mail and Chat functions to be very well integrated and it runs much faster on my computer than Opera did, and with less hassle.

I do like Opera though, and I expect to play with it some more someday on a new computer that can handle the heavier apps.

---

### Post by mips on 2012-07-22
> **Welly Wu said:**
> I figured out how to turn on GPU hardware acceleration and WebGL in Opera 12. Now, it is much faster and it works. This is great.

Mind sharing?

Have not tried Opera in ages but I'm about to install it for a test run just to see what the woo-ha is about ;)

---

### Post by Welly Wu on 2012-07-22
See my post #8 to learn how to turn on GPU hardware acceleration and WebGL in Opera 12.00.

---

### Post by Phrea on 2012-07-22
I've always used Opera, so I'm very happy with it.  

...but, when I turned on hardware acceleration, it did this: [http://i.imgur.com/KB1EQ.jpg](http://i.imgur.com/KB1EQ.jpg), so I won't be doing that again any time soon.

---

### Post by neu5eeCh on 2012-07-22
> **BigSilly said:**
> Well I'll consider myself alone then. I found Opera to be quite a bit overrated by its fans, being more than a bit buggy in the interface department, and often hanging indefinitely when trying to access sites. I gave it a good go, but it's still very much Firefox for me.

You're not alone. I would *like* to like Opera, but it's never worked on any of my systems (the various Ubuntu upgrades). For example: Every time I upgrade Opera it simply stops working. If I try to run it from the command line, from its _very_ install directory, a brief spin of the hard drive ends in airy nothing. I just find this bug so irritating I can't even be bothered to investigate or solve it. Why should I when a slew of other browsers work just fine? The other problem with Opera is that it doesn't work with Wordpress.com blogs (in the sense of content creation). For example, if I want to add an image to a post, Opera fails to bring up a dialogue box (in a separate window). To me, this is so lacking and slack that I can't even be bothered.

---

### Post by Welly Wu on 2012-07-23
Opera 12.00 has some problems playing movie trailers such as Batman: The Dark Knight Rises (which I saw with my father last night and it was terrific). Opera also crashes on a number of occasions. I still find it to be useful and I will continue to use it as my primary web browser.

I am getting really used to the built-in mail, news, chat, and RSS clients. They are quite useful and it saves me time and hassles from switching among multiple software applications.

Opera is energy efficient and memory efficient. I saved about 10 - 15 minutes of battery life and I also saved about 1.0 - 1.5 GB of RAM while using Opera 12.00. Future improvements in these areas will be nice with future versions.

I am happy with Opera 12.00 overall. I think that it is a fine web browser for general purpose usage and it is strikingly fast.

---

