# Intel8051-emulator
This is a development board for the Intel 8051 microcontroller which I made in the 1990's. It runs on Apple2 and uses the computer as a terminal to write programs in 8051 machine code, to disassemble the code and then to upload the program and to start/stop the 8051 processor. The card has a 40-pin connector on a ribbon cable, which is to be insetred in the target electronics which would run under the 8051 program. The benefit is that programs can be written and tested on the Apple2 which makes version turnaround time much faster - there is no need to eraze/flash the MCU for every test of the program.

Thery of operation

The Intel 8051 MCU is a microcontroller with 4 8-bit GPIOs and internal 8kB program ROM. The ROM is usially one-time programmable. There was a 8751 version manufactured which has a UV EPROM inside with a small galss window which allowed the program to be erazed and re-programmed. This made it possible to change and fine-tune the programs used. Additionally, a version with a piggy-back 28-pin connector for the EPROM was produced in small batches. I got hold of one such device and it was very easy to change the program by erazing and reprogramming the EPROM.

After some time I had the idea to start using an SRAM memory 6264 fo that it was even easier to change the program. I had to design some elctronics, by which the SRAM memory would be shared between the MCU and a comouter for the user interface. Naturally I used an Apple2.

The SRAM memory is connected to the piggy-back connector via a ribbon cable. It can de addressed either by the MCU in Read mode or by the Apple2 in Write mode. This is managed by a '74 trigger and some '244 buffers. Upon reset the default mode is access by the Apple2, this is also done with access to $C0N0. With a program switch access to $C0N1, the SRAM access is flipped to the MCU. This is also tied to the reset line of the MCU, so reset is released and the MCU starts the program in the SRAM.

When the Apple2 has access to the SRAM - an SRAM memory location can be written to by writing 3 bytes - address low 8 bits to $C0N2, address high 5 bits to $C0N3 and then data 8 bits to $C0N4.

The .dsk contains a disassembler for the machine code of the microcontroller and a program which manages transfers from the Apple2 RAM to the SRAM and starts the 8051 MCU.

Copyright (c) 2022 Ralle Palaveev All rights reserved.

Redistribution and use in source, binary, and manufactued forms, with or without modification, are permitted provided that the following conditions are met:

    Redistributions of source code and design files must retain the above copyright notice, this list of conditions and the following disclaimer.
    Redistributions in binary or manufactured form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
    All advertising materials mentioning features or use of this software or hardware must display the following acknowledgement: This product includes software and hardware developed by Ralle Palaveev.
    Neither the name of Ralle Palaveev nor the names of its contributors may be used to endorse or promote products derived from this software or hardware without specific prior written permission.

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
