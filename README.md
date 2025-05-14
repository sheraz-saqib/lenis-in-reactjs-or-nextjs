Smooth Scrolling in React or Next.js with Lenis
This guide explains how to implement smooth scrolling in a React or Next.js application using the @studio-freight/react-lenis package. Lenis provides a lightweight, customizable solution for achieving buttery-smooth scrolling with minimal setup.

Prerequisites

A React or Next.js project set up.
Node.js and npm installed.
Basic understanding of React/Next.js component structure.


Step 1: Install the Lenis Package
Install the @studio-freight/react-lenis package via npm:
npm install @studio-freight/react-lenis

This package provides a React-specific wrapper for Lenis, enabling smooth scrolling with customizable options.

Step 2: Create the SmoothScrolling Component
Create a new file named SmoothScrolling.jsx in your project's components directory (e.g., src/components/SmoothScrolling.jsx).

Step 3: Add the SmoothScrolling Component Code
Depending on your framework (React or Next.js), use the appropriate code below for the SmoothScrolling.jsx component. This component wraps your app's content to enable smooth scrolling.
For React.js
import { ReactLenis } from '@studio-freight/react-lenis';

function SmoothScrolling({ children }) {
  return (
    <ReactLenis root options={{ lerp: 0.1, duration: 1.2, smoothTouch: true }}>
      {children}
    </ReactLenis>
  );
}

export default SmoothScrolling;

For Next.js
Since Next.js uses server-side rendering by default, you must add the "use client" directive for client-side interactivity:
"use client";
import { ReactLenis } from '@studio-freight/react-lenis';

function SmoothScrolling({ children }) {
  return (
    <ReactLenis root options={{ lerp: 0.1, duration: 1.2, smoothTouch: true }}>
      {children}
    </ReactLenis>
  );
}

export default SmoothScrolling;

Configuration Options Explained

lerp: 0.1: Controls the smoothness of the scroll. Lower values (e.g., 0.05–0.2) create a smoother, more gradual scroll effect.
duration: 1.2: Sets the duration (in seconds) for scroll animations. Adjust this to make scrolling faster or slower.
smoothTouch: true: Enables smooth scrolling on touch devices. Set to false if you want to disable this for mobile users.

You can customize these options further based on your project's needs. Refer to the Lenis documentation for additional settings.

Step 4: Integrate the SmoothScrolling Component
Wrap your application's content with the SmoothScrolling component to apply smooth scrolling globally. In Next.js, this is typically done in the root layout file.
Example: Next.js Root Layout
Update your app/layout.jsx (or app/layout.tsx) file to include the SmoothScrolling component:
import SmoothScrolling from '@/components/SmoothScrolling';

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body className="antialiased">
        <SmoothScrolling>{children}</SmoothScrolling>
      </body>
    </html>
  );
}

Example: React.js Root Component
For a React.js app, wrap the SmoothScrolling component in your root component (e.g., src/App.jsx):
import SmoothScrolling from './components/SmoothScrolling';

function App() {
  return (
    <SmoothScrolling>
      {/* Your app content */}
    </SmoothScrolling>
  );
}

export default App;


Step 5: Test Your Application

Run your development server:npm run dev


Verify that scrolling is smooth across your application, including on touch devices if smoothTouch is enabled.
Adjust the lerp, duration, or other options in SmoothScrolling.jsx to fine-tune the scrolling experience.


Troubleshooting

Smooth scrolling not working:
Ensure the @studio-freight/react-lenis package is installed correctly.
Verify that the "use client" directive is included in Next.js for client-side rendering.
Check for conflicting CSS (e.g., overflow: hidden or position: fixed) that might interfere with scrolling.


Performance issues:
Reduce the lerp value for a less intensive animation.
Disable smoothTouch if touch scrolling feels sluggish on low-end devices.


TypeScript errors:
If using TypeScript, ensure you have the correct types installed:npm install @types/studio-freight__react-lenis






Additional Notes

Customization: Lenis supports advanced features like scroll triggers and custom easing. Explore the Lenis documentation for more details.
Compatibility: The @studio-freight/react-lenis package works seamlessly with both React and Next.js, but ensure your project is using a compatible version of React (18+ recommended).
Styling: The antialiased class in the layout ensures text rendering is smooth, but you can add additional Tailwind CSS or custom styles as needed.

For further assistance, refer to the Lenis GitHub repository or raise an issue in your project’s repository.
