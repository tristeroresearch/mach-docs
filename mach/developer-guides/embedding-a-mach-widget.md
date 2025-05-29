# Mach Exchange Embed Integration

The application supports being embedded into third-party websites via an iframe. Use the `/embed` path to access the embed-specific version of the application.

## URL Parameters for Customization

The embed version accepts the following URL parameters for customization:

### Theme Customization

- `themePrimary`: Primary color for buttons (hex format, e.g., `%23349FFD` for #349FFD)
- `themeBackground`: Background color (hex format)
- `showBranding`: Whether to show "Powered by Mach.Exchange" (default: `true`)
- `hideAIInput`: Whether to hide the AI input box (default: `false`)
- `useIntuitiveColorDefaults`: Whether to use automatic color complementary pairing when only one color is provided (default: `false`). When both primary and background colors are provided, this parameter has no effect.

### Logo Customization

- `logoUrl`: URL of the partner logo to display (URL-encoded)
- `logoHeight`: Height of the logo in pixels (numeric value, default: 40)
- `logoWidth`: Width of the logo in pixels (numeric value, optional)
- `logoPosition`: Alignment of the logo, options: `left`, `center`, or `right` (default: `center`)

### Pending Transaction Indicator

- `showPendingTX`: Whether to show the pending transaction indicator (default: `true`)
- `pendingTXPosition`: Position of the pending transaction indicator, options: `left`, `center`, or `right` (default: opposite to logo)

### Token Configuration

- `chains`: Comma-separated list of chain IDs to restrict available networks
- `from`: Source token in format `chainId:tokenAddress`
- `to`: Destination token in format `chainId:tokenAddress`
- `destinationWallet`: Custom recipient wallet address for receiving tokens (enables "Send to different wallet" mode)

## Example URLs

### Embed with primary color, backgrounds, hidden AI input, and destination wallet
```
https://app.mach.exchange/embed?themePrimary=%23AB0044&themeBackground=%23222222&themeModalBackground=%23001A1A&hideAIInput=true&destinationWallet=0x742d35Cc6609C2fBCbC69b7a0bF0c8B7dE0b1234
```

### Embed with backgrounds, destination wallet, and using intuitive color defaults
```
https://app.mach.exchange/embed?themeBackground=%23222222&themeModalBackground=%23001A1A&sellChain=10&sellToken=0x0b2C639c533813f4Aa9D7837CAf62653d097Ff85&buyChain=42161&buyToken=0xaf88d065e77c8cC2239327C5EDb3A432268e5831&useIntuitiveColorDefaults=true&destinationWallet=0x742d35Cc6609C2fBCbC69b7a0bF0c8B7dE0b1234
```

### Embed with backgrounds, hidden AI input, without intuitive color defaults, hiding the pending transaction indicator
```
https://app.mach.exchange/embed?themeBackground=%23222222&themeModalBackground=%23001A1A&sellChain=10&sellToken=0x0b2C639c533813f4Aa9D7837CAf62653d097Ff85&buyChain=42161&buyToken=0xaf88d065e77c8cC2239327C5EDb3A432268e5831&hideAIInput=true
```

## Integration Example

To embed Mach Exchange into your website, use an iframe:

```html
<iframe 
  src="https://app.mach.exchange/embed?hideAIInput=true&destinationWallet=YOUR_WALLET_ADDRESS" 
  width="100%" 
  height="600" 
  frameborder="0">
</iframe>
```

## Notes

- All color values should be URL-encoded (e.g., `%23` instead of `#`)
- The `destinationWallet` parameter enables "Send to different wallet" mode, allowing users to send tokens to a specified address
- When `hideAIInput=true`, the AI-powered input interface will be hidden for a more streamlined experience
- Logo URLs must be properly URL-encoded
- Chain IDs should correspond to supported networks
- Token addresses should be valid contract addresses for the specified chains 