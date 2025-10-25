# F5 LTM Demo Environment

A modern, responsive web application designed for demonstrating F5 Local Traffic Manager (LTM) load balancing functionality. This project provides a visually appealing interface that displays real-time server information, making it ideal for testing and showcasing load balancer configurations.

![F5 LTM Demo](https://img.shields.io/badge/demo-live-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## 🌟 Features

- **Real-time Server Information Display**
  - Server hostname
  - Request timestamp (ISO 8601 format)
  - Request URI
  - Source IP address
  - X-Forwarded-For (XFF) header
  - User-Agent information

- **Interactive Network Architecture Diagram**
  - Animated traffic flow visualization
  - Live server status indicators
  - Visual representation of load balancer distribution
  - Current server highlighting

- **Modern UI/UX**
  - Responsive Bootstrap 5.3 design
  - Smooth animations and transitions
  - Mobile-friendly layout
  - Custom gradient themes
  - Font Awesome icons

- **Customizable Gallery Section**
  - Display custom images or screenshots
  - Side-by-side image layout
  - Hover effects and transitions

## 🚀 Quick Start

### Prerequisites

- Web server (NGINX, Apache, or similar)
- Basic knowledge of web server configuration

### Add Multiple IP Addresses on Debian Linux

#### For Debian 11+ (using systemd-networkd or NetworkManager)

Edit `/etc/network/interfaces`:
```bash
sudo nano /etc/network/interfaces
```

Add the following:
```
auto eth0
iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    gateway 192.168.1.1

auto eth0:1
iface eth0:1 inet static
    address 192.168.1.11
    netmask 255.255.255.0

auto eth0:2
iface eth0:2 inet static
    address 192.168.1.12
    netmask 255.255.255.0

auto eth0:3
iface eth0:3 inet static
    address 192.168.1.13
    netmask 255.255.255.0
```

Restart networking:
```bash
sudo systemctl restart networking
```

**Note:** Replace `eth0` with your actual interface name.

### Generate SSL Certificate

Create a self-signed SSL certificate with RSA 2048-bit key (no password):
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout private.key -out certificate.crt \
  -subj "/C=US/ST=State/L=City/O=Organization/CN=example.com"
```

**Parameters:**
- `-x509` - Output a self-signed certificate
- `-nodes` - No DES (no password on private key)
- `-days 365` - Certificate valid for 1 year
- `-newkey rsa:2048` - Generate new RSA key with 2048 bits
- `-keyout` - Output file for private key
- `-out` - Output file for certificate
- `-subj` - Certificate subject (customize as needed)

**Output files:**
- `private.key` - Private key (no password)
- `certificate.crt` - Self-signed certificate

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/webserverdude/ltm-demo-html.git
   cd ltm-demo-html
   ```
2. **Deploy to your web server**
   ```bash
   # Example for NGINX
   sudo cp -r * /var/www/html/
   ```

3. **Configure your web server** (see NGINX configuration below)

## ⚙️ NGINX Configuration

### Basic Setup with Variable Substitution

The configuration includes HTTP as well as HTTPS listeners.
Add this configuration to your NGINX server block:

```
```

## 📁 Project Structure

```
ltm-demo-html/
├── index_red.html          # Server 1 (Red theme)
├── index_blue.html         # Server 2 (Blue theme)
├── index_green.html        # Server 3 (Green theme)
├── styles_red.css          # CSS for red theme
├── styles_blue.css         # CSS for blue theme
├── styles_green.css        # CSS for green theme
├── scripts.js              # JavaScript functionality
├── dummy.jpg               # Placeholder images
└── README.md               # This file
```

## 🔧 Template Variables

The following template variables are automatically replaced by NGINX:

| Variable | NGINX Variable | Description |
|----------|----------------|-------------|
| `{{server_name}}` | `$hostname` | Server hostname |
| `{{time_iso8601}}` | `$time_iso8601` | Current timestamp in ISO 8601 format |
| `{{request_uri}}` | `$request_uri` | Full request URI with arguments |
| `{{remote_addr}}` | `$remote_addr` | Client IP address |
| `{{http_x_forwarded_for}}` | `$http_x_forwarded_for` | X-Forwarded-For header value |
| `{{http_user_agent}}` | `$http_user_agent` | User-Agent header value |

## 📦 Dependencies

All dependencies are loaded via CDN:

- **Bootstrap 5.3.0** - UI framework
- **Font Awesome 6.4.0** - Icons
- **Animate.css 4.1.1** - CSS animations
- **Google Fonts (Inter + JetBrains Mono)** - Typography

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Note:** This is a demo application for testing and development purposes. It is not an official F5 Networks product.