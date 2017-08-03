USB ID translator
=================

# Purpose

Translate numeric USB device ID and interface representations into human readable strings by leveraging information from the USD ID database (http://www.linux-usb.org/usb.ids).

## Vendor & Product ID

Format: Two 16 bit numbers, separated by a colon; `0000:0000` ... `ffff:ffff`

First number represents vendor ID.
Second number represents product ID.

## Interface

Format: 3 bytes, separated by a colon; `0000:0000:0000` ... `ffff:ffff:ffff`

First number represents interface class.
Second number represents interface subclass.
Third number represents interface protocol.

# API
```c++
 class USBIDs
 {
 public:
   USBIDs(const std::string& filepath = "/usr/share/hwdata/usb.ids");

   std::string idToString(uint16_t vid, uint16_t pid);
   std::string interfaceToString(uint16_t c, uint16_t s, uint16_t p);
 };
 ```

# Implementation Notes
Latest `usb.ids` file can be downloaded from [http://www.linux-usb.org/](http://www.linux-usb.org/usb.ids).
Alternatively, the file can be installed via packages:

### Fedora
`$ dnf isntall hwdata`
### Arch Linux
`$ pacman -Sy hwids`
### Ubuntu
`$ apt install hwdata`

After successfull installation, the `usb.ids` file will be located at `/usr/share/hwdata/usb.ids`.
