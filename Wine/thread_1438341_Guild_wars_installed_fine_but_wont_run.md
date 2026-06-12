---
title: "Guild wars installed fine but wont run"
date: 2010-03-24
forum: Wine
---

### Post by klingensmith on 2010-03-24
here is the terminal output


2) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #37: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #38: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #41: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #42: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #45: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #46: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #49: "Error: 2001: Syntax error.\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #50: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #53: "Error: 2001: Syntax error.\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #54: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #57: "Error: 2001: Syntax error.\n"
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #58: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #60: "Error: 2001: Syntax error.\n"
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #61: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #64: "Error: 2001: Syntax error.\n"
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #65: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader
rint_glsl_info_log Error received from GLSL shader #67: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #68: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #70: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #71: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #74: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #75: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #77: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #78: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #81: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #84: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #87: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #88: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #91: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #92: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #94: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #95: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #98: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #99: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #102: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #103: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #105: "Error: 2001: Syntax error.\n"
fixme:d3d_shaderrint_glsl_info_log Error received from GLSL shader #106: "linking with uncompiled shader\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Find glsl program uniform locations @ glsl_shader.c / 3225
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3229
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3092
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3315
fixme:d3d_shader:shader_glsl_load_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUniform4fvARB @ glsl_shader.c / 410
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
captain@bookshelf:~$

---

### Post by klingensmith on 2010-03-24
I have a radeon 9600 graphics card

---

### Post by asdfoo on 2010-03-25
> **klingensmith said:**
> I have a radeon 9600 graphics card

you can try updating to the latest video drivers & wine version (1.1.41) that are available

---

### Post by AllRadioisDead on 2010-03-25
You should put the output on [code] tags.

---

### Post by _h_ on 2010-03-25
I'm seeing alot of shader errors in that output.

---

### Post by beastrace91 on 2010-03-25
> **_h_ said:**
> I'm seeing alot of shader errors in that output.

Thats normal for Wine output.

FYI the culprit of your game not running odds are is the fact that you have an ATI card. Best advice is to try different driver versions, sometimes you get lucky. But in general ATI drivers suck (doubly so on Linux)

~Jeff

---

