# STM32F407_DFU_BOOT
This code for STM32F407 jump to system memory bootloader from USB CDC ACM. To jump system memory, USB CDC need to detect BAUDRATE = 1200 and PARITY = ODD . I used picocom(linux) to jump into sysmem bootloader.

```shell
picocom /dev/ttyACM0 -b 1200 -y o
```

 Picocom will closed immediately because USB CDC closed and changed into USB DFU. For flashing firmware i used dfu-util.

```shell
sudo dfu-util -d 0483:df11 -a 0 -s 0x08000000:leave -D build/CDC2DFU.bin
```

