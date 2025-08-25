# Azure Web App Settings Converter

A simple web application that converts Azure Web App application settings from Windows format to Linux format.

## Overview

When migrating Azure Web Apps from Windows to Linux, application settings with colons (`:`) in their names need to be converted to use double underscores (`__`) instead, as Linux environments handle these characters differently.

This tool provides a convenient web interface to automatically convert your application settings JSON format.

## Features

- **Real-time conversion**: Paste your Windows-formatted settings and see the Linux-compatible format instantly
- **Simple interface**: Clean, intuitive design with visual indicators for Windows and Linux formats
- **Client-side processing**: All conversion happens in your browser - no data is sent to any server
- **Copy-paste friendly**: Easy to copy the converted settings for use in your Azure configuration

## How to Use

1. **Open the application**: Visit the [live application](https://zetes-swf.github.io/webapp-linux-settings-converter/)
2. **Paste Windows settings**: In the left textarea (Windows Settings), paste your application settings JSON
3. **Get Linux format**: The right textarea (Linux Settings) will automatically show the converted format
4. **Copy the result**: Copy the converted settings from the right textarea

## Example

**Input (Windows format):**
```json
{
  "name": "MyApp:Database:ConnectionString",
  "value": "Server=localhost;Database=mydb"
}
```

**Output (Linux format):**
```json
{
  "name": "MyApp__Database__ConnectionString", 
  "value": "Server=localhost;Database=mydb"
}
```

## Technical Details

The converter specifically targets the `"name"` fields in JSON objects and replaces all colons (`:`) with double underscores (`__`). This transformation is necessary because:

- Windows Azure Web Apps support colons in application setting names
- Linux Azure Web Apps treat colons as hierarchical separators and require double underscores instead

## Development

This is a static web application built with:
- HTML5
- CSS3 with [Chota CSS framework](https://jenil.github.io/chota/)
- Vanilla JavaScript
- FontAwesome icons via icongr.am

### Local Development

Since this is a static web application, you can simply open `index.html` in your browser or serve it with any static web server:

```bash
# Using Python's built-in server
python -m http.server 8000

# Using Node.js http-server
npx http-server

# Or simply open index.html in your browser
```

### Deployment

The application is automatically deployed to GitHub Pages via GitHub Actions when changes are pushed to the `main` branch.

## License

This project is open source. Feel free to use, modify, and distribute as needed.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.