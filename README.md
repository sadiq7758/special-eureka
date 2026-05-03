name: Build Flutter APK

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Setup Flutter
      uses: subosito/flutter-action@v2
      with:
        flutter-version: '3.19.0'

    - name: import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input";

export default function App() { const [page, setPage] = useState("home");

return ( <div className="min-h-screen bg-gray-100 p-4"> <header className="text-center mb-4"> <h1 className="text-2xl font-bold">SADIQ DATA HUB 🔥</h1> <p className="text-sm text-gray-600">Data • Airtime • Recharge Card</p> </header>

{page === "home" && (
    <div className="grid gap-3">
      <Card>
        <CardContent className="p-4">
          <h2 className="font-bold">Welcome 👋</h2>
          <p className="text-sm">Fast & affordable digital services</p>
        </CardContent>
      </Card>

      <Button onClick={() => setPage("buyData")}>Buy Data</Button>
      <Button onClick={() => setPage("airtime")}>Buy Airtime</Button>
      <Button onClick={() => setPage("recharge")}>Recharge Card</Button>
    </div>
  )}

  {page === "buyData" && (
    <Card>
      <CardContent className="p-4 space-y-3">
        <h2 className="font-bold">Buy Data</h2>
        <Input placeholder="Phone Number" />
        <Input placeholder="Network (MTN, Airtel...)" />
        <Input placeholder="Data Plan" />
        <Button>Pay & Buy (Paystack)</Button>
        <Button variant="secondary" onClick={() => setPage("home")}>Back</Button>
      </CardContent>
    </Card>
  )}

  {page === "airtime" && (
    <Card>
      <CardContent className="p-4 space-y-3">
        <h2 className="font-bold">Buy Airtime</h2>
        <Input placeholder="Phone Number" />
        <Input placeholder="Amount" />
        <Button>Pay & Buy</Button>
        <Button variant="secondary" onClick={() => setPage("home")}>Back</Button>
      </CardContent>
    </Card>
  )}

  {page === "recharge" && (
    <Card>
      <CardContent className="p-4 space-y-3">
        <h2 className="font-bold">Recharge Card</h2>
        <Input placeholder="Network" />
        <Input placeholder="Amount" />
        <Button>Generate Card</Button>
        <Button variant="secondary" onClick={() => setPage("home")}>Back</Button>
      </CardContent>
    </Card>
  )}

  <footer className="text-center text-xs text-gray-500 mt-6">
    © 2026 SADIQ Data Hub
  </footer>
</div>

); }Install dependencies
      run: flutter pub get

    - name: Build APK
      run: flutter build apk --release

    - name: Upload APK
      uses: actions/upload-artifact@v4
      with:
        name: vtu-app-apk
        path: build/app/outputs/flutter-apk/app-release.