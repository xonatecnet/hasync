# HAsync - Home Assistant Manager

Advanced Home Assistant management interface with client pairing and entity synchronization.

## About

HAsync provides a powerful web interface and API for managing Home Assistant, enabling:

- Client device pairing and management
- Entity synchronization across clients
- Real-time updates via WebSocket
- Secure JWT authentication
- RESTful API for programmatic access

## Configuration

### Options

- **jwt_secret** (required): Secret key for JWT token signing. Change this in production!
- **database_path** (optional): Path to SQLite database file (default: `/data/hasync.db`)
- **log_level** (optional): Logging verbosity (debug, info, warn, error) (default: `info`)
- **max_clients** (optional): Maximum number of connected clients (default: `100`)
- **rate_limit** (optional): API rate limit requests per hour (default: `500`)

### Example Configuration

```yaml
jwt_secret: "your-very-long-and-secure-random-string-here"
database_path: "/data/hasync.db"
log_level: "info"
max_clients: 150
rate_limit: 1000
```

## Installation

1. Add this repository to your Home Assistant add-on store:
   ```
   https://github.com/xonatecnet/hasync
   ```

2. Install the "HAsync - Home Assistant Manager" add-on

3. Configure the add-on (especially change the `jwt_secret`!)

4. Start the add-on

5. Access the web interface via Ingress or at `http://YOUR_HA_IP:5173`

## Usage

### Web Interface

The web interface is available at:
- Via Ingress: Click "OPEN WEB UI" in the add-on page
- Direct access: `http://YOUR_HA_IP:5173`

### API Endpoints

The backend API runs on port 8099:

- `GET /health` - Health check endpoint
- `POST /api/auth/login` - Authenticate and get JWT token
- `GET /api/clients` - List paired clients
- `POST /api/clients` - Pair a new client
- `GET /api/entities` - Get synchronized entities
- WebSocket at `ws://YOUR_HA_IP:8099/ws` - Real-time updates

## Support

For issues and feature requests, please visit:
https://github.com/xonatecnet/hasync/issues
