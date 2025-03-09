# Konfigurasi Jaringan - Cisco Packet Tracer

## 1. Informasi Jaringan
- **Router:** College
- **Switch:** Class-B
- **PCs:** Student-1, Student-2, Student-3, Student-4
- **Subnet A:** 128.107.20.0/24
- **Subnet B:** 128.107.30.0/24

---

## 2. Konfigurasi Router (College)
### **Konfigurasi Interface**
```plaintext
configure terminal

interface GigabitEthernet0/0
 ip address 128.107.20.1 255.255.255.0
 ipv6 address 2001:DB8:A::1/64
 no shutdown

interface GigabitEthernet0/1
 ip address 128.107.30.1 255.255.255.0
 ipv6 address 2001:DB8:B::1/64
 no shutdown

exit
```

### **Konfigurasi Routing**
```plaintext
ip route 0.0.0.0 0.0.0.0 128.107.20.1
ipv6 route ::/0 2001:DB8:A::1
```

### **Konfigurasi Keamanan**
```plaintext
enable secret class
line console 0
 password cisco
 login
exit
```

### **Konfigurasi Banner MOTD**
```plaintext
banner motd # Authorized Access Only #
```

---

## 3. Konfigurasi Switch (Class-B)
### **Konfigurasi VLAN & IP Default Gateway**
```plaintext
configure terminal

interface vlan 1
 ip address 128.107.30.15 255.255.255.0
 no shutdown

ip default-gateway 128.107.30.1

exit
```

---

## 4. Konfigurasi PC (Student-1, Student-2, Student-3, Student-4)
### **Subnet A (Student-1 & Student-2)**
- **IP Address:** 128.107.20.25 / 128.107.20.26
- **Subnet Mask:** 255.255.255.0
- **Default Gateway:** 128.107.20.1

### **Subnet B (Student-3 & Student-4)**
- **IP Address:** 128.107.30.25 / 128.107.30.26
- **Subnet Mask:** 255.255.255.0
- **Default Gateway:** 128.107.30.1

---

## 5. Pengujian Koneksi
### **Cek IP di PC**
```plaintext
ipconfig
```

### **Ping Router dari PC**
```plaintext
ping 128.107.20.1
ping 128.107.30.1
```

### **Cek Routing di Router**
```plaintext
show ip route
show ipv6 route
```

### **Save Konfigurasi**
```plaintext
copy running-config startup-config
```
