# Moto-back-up
My MoTo Ride App First Draft

import 'package:flutter/material.dart';

void main() {
  runApp(const MoToApp());
}

const Color motoPurple = Color(0xFF6C3CE9);
const Color motoDark = Color(0xFF19152B);
const Color motoBackground = Color(0xFFF7F5FC);

class MoToApp extends StatelessWidget {
  const MoToApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'MoTo',
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        useMaterial3: true,
        scaffoldBackgroundColor: motoBackground,
        colorScheme: ColorScheme.fromSeed(
          seedColor: motoPurple,
          brightness: Brightness.light,
        ),
        fontFamily: 'Arial',
      ),
      home: const WelcomeScreen(),
    );
  }
}

class WelcomeScreen extends StatelessWidget {
  const WelcomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Center(
          child: SingleChildScrollView(
            padding: const EdgeInsets.all(24),
            child: ConstrainedBox(
              constraints: const BoxConstraints(maxWidth: 460),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.stretch,
                children: [
                  const SizedBox(height: 30),
                  Container(
                    height: 100,
                    width: 100,
                    alignment: Alignment.center,
                    decoration: BoxDecoration(
                      color: motoPurple,
                      borderRadius: BorderRadius.circular(30),
                      boxShadow: [
                        BoxShadow(
                          color: motoPurple.withValues(alpha: 0.2),
                          blurRadius: 25,
                          offset: const Offset(0, 10),
                        ),
                      ],
                    ),
                    child: const Icon(
                      Icons.route_rounded,
                      color: Colors.white,
                      size: 56,
                    ),
                  ),
                  const SizedBox(height: 22),
                  const Text(
                    'MoTo',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 42,
                      fontWeight: FontWeight.w900,
                      color: motoDark,
                      letterSpacing: 1.5,
                    ),
                  ),
                  const SizedBox(height: 8),
                  const Text(
                    'Your journey, your way.',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      fontSize: 17,
                      color: Colors.black54,
                    ),
                  ),
                  const SizedBox(height: 35),
                  Container(
                    padding: const EdgeInsets.all(22),
                    decoration: BoxDecoration(
                      gradient: const LinearGradient(
                        colors: [Color(0xFF7650F0), Color(0xFF4F24C7)],
                        begin: Alignment.topLeft,
                        end: Alignment.bottomRight,
                      ),
                      borderRadius: BorderRadius.circular(24),
                    ),
                    child: const Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Icon(
                          Icons.location_on_rounded,
                          color: Colors.white,
                          size: 32,
                        ),
                        SizedBox(height: 16),
                        Text(
                          'Where are we going?',
                          style: TextStyle(
                            color: Colors.white,
                            fontSize: 24,
                            fontWeight: FontWeight.bold,
                          ),
                        ),
                        SizedBox(height: 8),
                        Text(
                          'Your next ride is just a few steps away.',
                          style: TextStyle(
                            color: Colors.white70,
                            fontSize: 15,
                          ),
                        ),
                      ],
                    ),
                  ),
                  const SizedBox(height: 28),
                  const Text(
                    'GET STARTED',
                    style: TextStyle(
                      color: Colors.black54,
                      fontSize: 12,
                      fontWeight: FontWeight.bold,
                      letterSpacing: 1.5,
                    ),
                  ),
                  const SizedBox(height: 14),
                  _RoleButton(
                    icon: Icons.person_rounded,
                    title: 'Ride with MoTo',
                    subtitle: 'Book a ride to your destination',
                    onTap: () {
                      Navigator.push(
                        context,
                        MaterialPageRoute(
                          builder: (_) => const RoleScreen(
                            isDriver: false,
                          ),
                        ),
                      );
                    },
                  ),
                  const SizedBox(height: 14),
                  _RoleButton(
                    icon: Icons.directions_car_rounded,
                    title: 'Drive with MoTo',
                    subtitle: 'Earn money on your own schedule',
                    onTap: () {
                      Navigator.push(
                        context,
                        MaterialPageRoute(
                          builder: (_) => const RoleScreen(
                            isDriver: true,
                          ),
                        ),
                      );
                    },
                  ),
                  const SizedBox(height: 28),
                  const Text(
                    'Launching in Port Harcourt, Lagos and Abuja',
                    textAlign: TextAlign.center,
                    style: TextStyle(
                      color: Colors.black54,
                      fontSize: 12,
                    ),
                  ),
                  const SizedBox(height: 12),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}

class _RoleButton extends StatelessWidget {
  final IconData icon;
  final String title;
  final String subtitle;
  final VoidCallback onTap;

  const _RoleButton({
    required this.icon,
    required this.title,
    required this.subtitle,
    required this.onTap,
  });

  @override
  Widget build(BuildContext context) {
    return Material(
      color: Colors.white,
      borderRadius: BorderRadius.circular(18),
      child: InkWell(
        onTap: onTap,
        borderRadius: BorderRadius.circular(18),
        child: Container(
          padding: const EdgeInsets.all(18),
          decoration: BoxDecoration(
            borderRadius: BorderRadius.circular(18),
            border: Border.all(color: const Color(0xFFE9E3F5)),
          ),
          child: Row(
            children: [
              Container(
                height: 52,
                width: 52,
                decoration: BoxDecoration(
                  color: const Color(0xFFF0EBFF),
                  borderRadius: BorderRadius.circular(16),
                ),
                child: Icon(icon, color: motoPurple, size: 28),
              ),
              const SizedBox(width: 15),
              Expanded(
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Text(
                      title,
                      style: const TextStyle(
                        fontSize: 16,
                        fontWeight: FontWeight.bold,
                        color: motoDark,
                      ),
                    ),
                    const SizedBox(height: 5),
                    Text(
                      subtitle,
                      style: const TextStyle(
                        fontSize: 12,
                        color: Colors.black54,
                      ),
                    ),
                  ],
                ),
              ),
              const Icon(
                Icons.arrow_forward_ios_rounded,
                color: motoPurple,
                size: 17,
              ),
            ],
          ),
        ),
      ),
    );
  }
}


class RoleScreen extends StatelessWidget {
  final bool isDriver;

  const RoleScreen({super.key, required this.isDriver});

  @override
  Widget build(BuildContext context) {
    if (!isDriver) {
      return const PassengerBookingScreen();
    }

    return const DriverRegistrationScreen();
  }
}

class DriverRegistrationScreen extends StatefulWidget {
  const DriverRegistrationScreen({super.key});

  @override
  State<DriverRegistrationScreen> createState() =>
      _DriverRegistrationScreenState();
}

class _DriverRegistrationScreenState
    extends State<DriverRegistrationScreen> {
  final _formKey = GlobalKey<FormState>();

  final _nameController = TextEditingController();
  final _phoneController = TextEditingController();
  final _emailController = TextEditingController();
  final _makeController = TextEditingController();
  final _modelController = TextEditingController();
  final _yearController = TextEditingController();
  final _colourController = TextEditingController();
  final _plateController = TextEditingController();

  bool _licenseChecked = false;
  bool _vehiclePapersChecked = false;
  bool _insuranceChecked = false;

  @override
  void dispose() {
    _nameController.dispose();
    _phoneController.dispose();
    _emailController.dispose();
    _makeController.dispose();
    _modelController.dispose();
    _yearController.dispose();
    _colourController.dispose();
    _plateController.dispose();
    super.dispose();
  }

  String? _required(String? value) {
    if (value == null || value.trim().isEmpty) {
      return 'This field is required';
    }
    return null;
  }

  Widget _field({
    required TextEditingController controller,
    required String label,
    required IconData icon,
    String? hint,
    TextInputType keyboardType = TextInputType.text,
    String? Function(String?)? validator,
  }) {
    return Padding(
      padding: const EdgeInsets.only(bottom: 15),
      child: TextFormField(
        controller: controller,
        keyboardType: keyboardType,
        validator: validator ?? _required,
        decoration: InputDecoration(
          labelText: label,
          hintText: hint,
          prefixIcon: Icon(icon, color: motoPurple),
          filled: true,
          fillColor: Colors.white,
          border: OutlineInputBorder(
            borderRadius: BorderRadius.circular(15),
            borderSide: const BorderSide(
              color: Color(0xFFE9E3F5),
            ),
          ),
          enabledBorder: OutlineInputBorder(
            borderRadius: BorderRadius.circular(15),
            borderSide: const BorderSide(
              color: Color(0xFFE9E3F5),
            ),
          ),
        ),
      ),
    );
  }

  Widget _sectionTitle(String title, String subtitle) {
    return Padding(
      padding: const EdgeInsets.only(top: 24, bottom: 15),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Text(
            title,
            style: const TextStyle(
              fontSize: 21,
              fontWeight: FontWeight.bold,
              color: motoDark,
            ),
          ),
          const SizedBox(height: 5),
          Text(
            subtitle,
            style: const TextStyle(
              color: Colors.black54,
              fontSize: 13,
            ),
          ),
        ],
      ),
    );
  }

  Widget _documentCheck({
    required String title,
    required String subtitle,
    required bool checked,
    required ValueChanged<bool?> onChanged,
  }) {
    return CheckboxListTile(
      value: checked,
      onChanged: onChanged,
      activeColor: motoPurple,
      contentPadding: const EdgeInsets.symmetric(horizontal: 4),
      controlAffinity: ListTileControlAffinity.leading,
      title: Text(
        title,
        style: const TextStyle(
          fontWeight: FontWeight.w600,
          color: motoDark,
        ),
      ),
      subtitle: Text(
        subtitle,
        style: const TextStyle(fontSize: 12),
      ),
    );
  }

  void _submitApplication() {
    if (!_formKey.currentState!.validate()) {
      return;
    }

    if (!_licenseChecked ||
        !_vehiclePapersChecked ||
        !_insuranceChecked) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(
          content: Text(
            'Please confirm that all three required documents '
            'are ready for submission.',
          ),
        ),
      );
      return;
    }

    showDialog<void>(
      context: context,
      barrierDismissible: false,
      builder: (dialogContext) {
        return AlertDialog(
          icon: const Icon(
            Icons.verified_user_outlined,
            color: motoPurple,
            size: 45,
          ),
          title: const Text('Application prepared!'),
          content: const Text(
            'Your demo driver application has passed the '
            'form checks. No personal details or documents '
            'have been uploaded or saved, and no verification '
            'has taken place yet.',
          ),
          actions: [
            FilledButton(
              onPressed: () {
                Navigator.pop(dialogContext);
                Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (_) => const DriverDashboardScreen(),
                  ),
                );
              },
              style: FilledButton.styleFrom(
                backgroundColor: motoPurple,
              ),
              child: const Text('Continue to dashboard'),
            ),
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Driver registration'),
        backgroundColor: motoBackground,
      ),
      body: SafeArea(
        child: Form(
          key: _formKey,
          child: ListView(
            padding: const EdgeInsets.all(20),
            children: [
              Container(
                padding: const EdgeInsets.all(22),
                decoration: BoxDecoration(
                  gradient: const LinearGradient(
                    colors: [
                      Color(0xFF7650F0),
                      Color(0xFF4F24C7),
                    ],
                  ),
                  borderRadius: BorderRadius.circular(22),
                ),
                child: const Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Icon(
                      Icons.directions_car_rounded,
                      color: Colors.white,
                      size: 42,
                    ),
                    SizedBox(height: 14),
                    Text(
                      'Become a MoTo driver',
                      style: TextStyle(
                        color: Colors.white,
                        fontSize: 25,
                        fontWeight: FontWeight.bold,
                      ),
                    ),
                    SizedBox(height: 8),
                    Text(
                      'Register your details and prepare your '
                      'vehicle documents for review.',
                      style: TextStyle(
                        color: Colors.white70,
                        fontSize: 14,
                      ),
                    ),
                  ],
                ),
              ),

              _sectionTitle(
                '1. Personal information',
                'Tell us who will be driving.',
              ),

              _field(
                controller: _nameController,
                label: 'Full legal name',
                icon: Icons.person_outline,
              ),
              _field(
                controller: _phoneController,
                label: 'Phone number',
                icon: Icons.phone_outlined,
                hint: 'e.g. 08012345678',
                keyboardType: TextInputType.phone,
                validator: (value) {
                  if (value == null || value.trim().isEmpty) {
                    return 'Enter your phone number';
                  }
                  final digits = value.replaceAll(
                    RegExp(r'[\s+()-]'),
                    '',
                  );
                  if (!RegExp(r'^\d{10,15}$').hasMatch(digits)) {
                    return 'Enter a valid phone number';
                  }
                  return null;
                },
              ),
              _field(
                controller: _emailController,
                label: 'Email address',
                icon: Icons.email_outlined,
                keyboardType: TextInputType.emailAddress,
                validator: (value) {
                  if (value == null || value.trim().isEmpty) {
                    return 'Enter your email address';
                  }
                  if (!RegExp(
                    r'^[^@\s]+@[^@\s]+\.[^@\s]+$',
                  ).hasMatch(value.trim())) {
                    return 'Enter a valid email address';
                  }
                  return null;
                },
              ),

              _sectionTitle(
                '2. Vehicle information',
                'MoTo is starting with cars only.',
              ),

              _field(
                controller: _makeController,
                label: 'Vehicle make',
                icon: Icons.directions_car_outlined,
                hint: 'e.g. Toyota, Honda, Hyundai',
              ),
              _field(
                controller: _modelController,
                label: 'Vehicle model',
                icon: Icons.car_rental_outlined,
                hint: 'e.g. Corolla, Accord, Elantra',
              ),
              _field(
                controller: _yearController,
                label: 'Vehicle year',
                icon: Icons.calendar_month_outlined,
                hint: 'e.g. 2021',
                keyboardType: TextInputType.number,
                validator: (value) {
                  if (value == null || value.trim().isEmpty) {
                    return 'Enter the vehicle year';
                  }
                  final year = int.tryParse(value.trim());
                  if (year == null ||
                      year < 1990 ||
                      year > DateTime.now().year + 1) {
                    return 'Enter a valid vehicle year';
                  }
                  return null;
                },
              ),
              _field(
                controller: _colourController,
                label: 'Vehicle colour',
                icon: Icons.palette_outlined,
              ),
              _field(
                controller: _plateController,
                label: 'Vehicle registration number',
                icon: Icons.confirmation_number_outlined,
                hint: 'Enter the plate number',
              ),

              _sectionTitle(
                '3. Required documents',
                'Confirm that these documents are ready. '
                    'Actual uploads will be added later.',
              ),

              Container(
                padding: const EdgeInsets.symmetric(
                  horizontal: 12,
                  vertical: 8,
                ),
                decoration: BoxDecoration(
                  color: Colors.white,
                  borderRadius: BorderRadius.circular(18),
                  border: Border.all(
                    color: const Color(0xFFE9E3F5),
                  ),
                ),
                child: Column(
                  children: [
                    _documentCheck(
                      title: "Driver's licence",
                      subtitle: 'Valid driving licence',
                      checked: _licenseChecked,
                      onChanged: (value) => setState(
                        () => _licenseChecked = value ?? false,
                      ),
                    ),
                    const Divider(height: 1),
                    _documentCheck(
                      title: 'Vehicle papers',
                      subtitle: 'Vehicle registration documents',
                      checked: _vehiclePapersChecked,
                      onChanged: (value) => setState(
                        () => _vehiclePapersChecked = value ?? false,
                      ),
                    ),
                    const Divider(height: 1),
                    _documentCheck(
                      title: 'Proof of insurance',
                      subtitle: 'Valid vehicle insurance',
                      checked: _insuranceChecked,
                      onChanged: (value) => setState(
                        () => _insuranceChecked = value ?? false,
                      ),
                    ),
                  ],
                ),
              ),

              const SizedBox(height: 16),
              Container(
                padding: const EdgeInsets.all(14),
                decoration: BoxDecoration(
                  color: const Color(0xFFF0EBFF),
                  borderRadius: BorderRadius.circular(14),
                ),
                child: const Row(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Icon(
                      Icons.shield_outlined,
                      color: motoPurple,
                    ),
                    SizedBox(width: 10),
                    Expanded(
                      child: Text(
                        'Safety first: before real drivers are approved, '
                        'MoTo must implement secure identity checks, '
                        'document review and vehicle verification.',
                        style: TextStyle(
                          fontSize: 12,
                          color: motoDark,
                        ),
                      ),
                    ),
                  ],
                ),
              ),

              const SizedBox(height: 22),
              SizedBox(
                width: double.infinity,
                child: FilledButton.icon(
                  onPressed: _submitApplication,
                  icon: const Icon(Icons.send_rounded),
                  label: const Text('Submit demo application'),
                  style: FilledButton.styleFrom(
                    backgroundColor: motoPurple,
                    padding: const EdgeInsets.symmetric(vertical: 17),
                    shape: RoundedRectangleBorder(
                      borderRadius: BorderRadius.circular(15),
                    ),
                  ),
                ),
              ),
              const SizedBox(height: 14),
              const Text(
                'DEVELOPMENT PREVIEW — no information is saved '
                'or sent to MoTo.',
                textAlign: TextAlign.center,
                style: TextStyle(
                  fontSize: 11,
                  color: Colors.black54,
                ),
              ),
              const SizedBox(height: 20),
            ],
          ),
        ),
      ),
    );
  }
}




class DriverDashboardScreen extends StatefulWidget {
  const DriverDashboardScreen({super.key});

  @override
  State<DriverDashboardScreen> createState() =>
      _DriverDashboardScreenState();
}

class _DriverDashboardScreenState
    extends State<DriverDashboardScreen> {
  bool isOnline = false;
  bool hasDemoRequest = true;
  bool requestAccepted = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'MoTo Driver',
          style: TextStyle(fontWeight: FontWeight.bold),
        ),
        backgroundColor: motoBackground,
        actions: [
          IconButton(
            tooltip: 'Back to home',
            onPressed: () => Navigator.pop(context),
            icon: const Icon(Icons.home_outlined),
          ),
        ],
      ),
      body: SafeArea(
        child: ListView(
          padding: const EdgeInsets.all(20),
          children: [
            const Text(
              'Welcome, Driver! 👋',
              style: TextStyle(
                fontSize: 26,
                fontWeight: FontWeight.bold,
                color: motoDark,
              ),
            ),
            const SizedBox(height: 6),
            const Text(
              'Your next journey starts with you.',
              style: TextStyle(color: Colors.black54),
            ),
            const SizedBox(height: 24),

            // Online/offline status
            Container(
              padding: const EdgeInsets.all(20),
              decoration: BoxDecoration(
                color: isOnline
                    ? const Color(0xFFE5F8EC)
                    : Colors.white,
                borderRadius: BorderRadius.circular(22),
                border: Border.all(
                  color: isOnline
                      ? const Color(0xFF92D9AB)
                      : const Color(0xFFE9E3F5),
                ),
              ),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Row(
                    children: [
                      Icon(
                        isOnline
                            ? Icons.radio_button_checked
                            : Icons.radio_button_off,
                        color: isOnline
                            ? Colors.green
                            : Colors.grey,
                        size: 28,
                      ),
                      const SizedBox(width: 12),
                      Expanded(
                        child: Column(
                          crossAxisAlignment:
                              CrossAxisAlignment.start,
                          children: [
                            Text(
                              isOnline
                                  ? 'You are online'
                                  : 'You are offline',
                              style: const TextStyle(
                                fontSize: 19,
                                fontWeight: FontWeight.bold,
                                color: motoDark,
                              ),
                            ),
                            const SizedBox(height: 5),
                            Text(
                              isOnline
                                  ? 'You can view demo ride requests.'
                                  : 'Go online when you are ready to drive.',
                              style: const TextStyle(
                                fontSize: 13,
                                color: Colors.black54,
                              ),
                            ),
                          ],
                        ),
                      ),
                    ],
                  ),
                  const SizedBox(height: 20),
                  SizedBox(
                    width: double.infinity,
                    child: FilledButton(
                      onPressed: () {
                        setState(() {
                          isOnline = !isOnline;
                          if (!isOnline) {
                            requestAccepted = false;
                          }
                        });
                      },
                      style: FilledButton.styleFrom(
                        backgroundColor:
                            isOnline ? Colors.redAccent : motoPurple,
                        padding: const EdgeInsets.symmetric(
                          vertical: 16,
                        ),
                        shape: RoundedRectangleBorder(
                          borderRadius: BorderRadius.circular(14),
                        ),
                      ),
                      child: Text(
                        isOnline ? 'Go offline' : 'Go online',
                        style: const TextStyle(
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                    ),
                  ),
                ],
              ),
            ),

            const SizedBox(height: 24),

            // Earnings card
            const Text(
              'YOUR PERFORMANCE',
              style: TextStyle(
                fontSize: 12,
                letterSpacing: 1.2,
                fontWeight: FontWeight.bold,
                color: Colors.black54,
              ),
            ),
            const SizedBox(height: 12),
            Container(
              padding: const EdgeInsets.all(22),
              decoration: BoxDecoration(
                gradient: const LinearGradient(
                  colors: [
                    Color(0xFF7650F0),
                    Color(0xFF4F24C7),
                  ],
                ),
                borderRadius: BorderRadius.circular(22),
              ),
              child: const Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Icon(
                    Icons.account_balance_wallet_rounded,
                    color: Colors.white70,
                    size: 30,
                  ),
                  SizedBox(height: 15),
                  Text(
                    'Today’s demo earnings',
                    style: TextStyle(
                      color: Colors.white70,
                      fontSize: 14,
                    ),
                  ),
                  SizedBox(height: 5),
                  Text(
                    '₦0.00',
                    style: TextStyle(
                      color: Colors.white,
                      fontSize: 34,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  SizedBox(height: 8),
                  Text(
                    'Your real earnings will appear after '
                    'completed trips are connected.',
                    style: TextStyle(
                      color: Colors.white70,
                      fontSize: 12,
                    ),
                  ),
                ],
              ),
            ),

            const SizedBox(height: 28),

            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                const Text(
                  'Ride requests',
                  style: TextStyle(
                    fontSize: 21,
                    fontWeight: FontWeight.bold,
                    color: motoDark,
                  ),
                ),
                if (isOnline && hasDemoRequest)
                  const Icon(
                    Icons.notifications_active_outlined,
                    color: motoPurple,
                  ),
              ],
            ),
            const SizedBox(height: 12),

            if (!isOnline)
              _driverMessage(
                icon: Icons.power_settings_new_rounded,
                title: 'You’re currently offline',
                message:
                    'Go online to see how ride requests will '
                    'appear on your dashboard.',
              )
            else if (!hasDemoRequest)
              _driverMessage(
                icon: Icons.check_circle_outline_rounded,
                title: 'You’re all caught up',
                message:
                    'There are no more demo requests to display.',
              )
            else if (requestAccepted)
              _driverMessage(
                icon: Icons.directions_car_rounded,
                title: 'Demo ride accepted!',
                message:
                    'This is a practice trip only. No passenger '
                    'has been contacted.',
              )
            else
              Container(
                padding: const EdgeInsets.all(18),
                decoration: BoxDecoration(
                  color: Colors.white,
                  borderRadius: BorderRadius.circular(20),
                  border: Border.all(
                    color: const Color(0xFFE9E3F5),
                  ),
                ),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Row(
                      children: [
                        const CircleAvatar(
                          backgroundColor: Color(0xFFF0EBFF),
                          child: Icon(
                            Icons.person_rounded,
                            color: motoPurple,
                          ),
                        ),
                        const SizedBox(width: 12),
                        const Expanded(
                          child: Column(
                            crossAxisAlignment:
                                CrossAxisAlignment.start,
                            children: [
                              Text(
                                'Demo passenger',
                                style: TextStyle(
                                  fontWeight: FontWeight.bold,
                                  color: motoDark,
                                ),
                              ),
                              SizedBox(height: 4),
                              Text(
                                'Sample ride request',
                                style: TextStyle(
                                  fontSize: 12,
                                  color: Colors.black54,
                                ),
                              ),
                            ],
                          ),
                        ),
                        const Text(
                          '₦2,500',
                          style: TextStyle(
                            fontSize: 18,
                            fontWeight: FontWeight.bold,
                            color: motoPurple,
                          ),
                        ),
                      ],
                    ),
                    const Divider(height: 28),
                    const Row(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Icon(
                          Icons.my_location_rounded,
                          color: motoPurple,
                          size: 20,
                        ),
                        SizedBox(width: 12),
                        Expanded(
                          child: Text('GRA, Port Harcourt'),
                        ),
                      ],
                    ),
                    const SizedBox(height: 14),
                    const Row(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Icon(
                          Icons.location_on_rounded,
                          color: Colors.redAccent,
                          size: 20,
                        ),
                        SizedBox(width: 12),
                        Expanded(
                          child: Text('Port Harcourt Airport'),
                        ),
                      ],
                    ),
                    const SizedBox(height: 20),
                    SizedBox(
                      width: double.infinity,
                      child: FilledButton.icon(
                        onPressed: () {
                          setState(() {
                            requestAccepted = true;
                          });
                        },
                        icon: const Icon(
                          Icons.check_circle_outline,
                        ),
                        label: const Text('Accept demo ride'),
                        style: FilledButton.styleFrom(
                          backgroundColor: motoPurple,
                          padding: const EdgeInsets.symmetric(
                            vertical: 15,
                          ),
                        ),
                      ),
                    ),
                    const SizedBox(height: 8),
                    SizedBox(
                      width: double.infinity,
                      child: OutlinedButton(
                        onPressed: () {
                          setState(() {
                            hasDemoRequest = false;
                          });
                        },
                        child: const Text('Dismiss demo request'),
                      ),
                    ),
                  ],
                ),
              ),

            const SizedBox(height: 24),
            const Text(
              'DEVELOPMENT PREVIEW',
              textAlign: TextAlign.center,
              style: TextStyle(
                fontSize: 11,
                letterSpacing: 1.1,
                color: Colors.black45,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 6),
            const Text(
              'Demo requests, status and earnings are not '
              'connected to real passengers or payments.',
              textAlign: TextAlign.center,
              style: TextStyle(
                fontSize: 12,
                color: Colors.black54,
              ),
            ),
          ],
        ),
      ),
    );
  }

  Widget _driverMessage({
    required IconData icon,
    required String title,
    required String message,
  }) {
    return Container(
      width: double.infinity,
      padding: const EdgeInsets.all(24),
      decoration: BoxDecoration(
        color: Colors.white,
        borderRadius: BorderRadius.circular(20),
        border: Border.all(
          color: const Color(0xFFE9E3F5),
        ),
      ),
      child: Column(
        children: [
          Icon(icon, size: 42, color: motoPurple),
          const SizedBox(height: 12),
          Text(
            title,
            textAlign: TextAlign.center,
            style: const TextStyle(
              fontSize: 17,
              fontWeight: FontWeight.bold,
              color: motoDark,
            ),
          ),
          const SizedBox(height: 8),
          Text(
            message,
            textAlign: TextAlign.center,
            style: const TextStyle(
              color: Colors.black54,
            ),
          ),
        ],
      ),
    );
  }
}


class PassengerBookingScreen extends StatefulWidget {
  const PassengerBookingScreen({super.key});

  @override
  State<PassengerBookingScreen> createState() =>
      _PassengerBookingScreenState();
}

class _PassengerBookingScreenState
    extends State<PassengerBookingScreen> {
  final pickupController = TextEditingController();
  final destinationController = TextEditingController();

  String selectedRide = 'MoTo Standard';
  bool showEstimate = false;

  final Map<String, int> sampleFares = {
    'MoTo Standard': 2500,
    'MoTo Comfort': 4000,
    'MoTo XL': 5500,
  };

  @override
  void dispose() {
    pickupController.dispose();
    destinationController.dispose();
    super.dispose();
  }

  void calculateEstimate() {
    FocusScope.of(context).unfocus();

    if (pickupController.text.trim().isEmpty ||
        destinationController.text.trim().isEmpty) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(
          content: Text('Enter both pickup and destination.'),
        ),
      );
      return;
    }

    if (pickupController.text.trim().toLowerCase() ==
        destinationController.text.trim().toLowerCase()) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(
          content: Text(
            'Pickup and destination must be different.',
          ),
        ),
      );
      return;
    }

    setState(() => showEstimate = true);
  }

  void requestDemoRide() {
    showDialog<void>(
      context: context,
      builder: (dialogContext) => AlertDialog(
        icon: const Icon(
          Icons.directions_car_rounded,
          color: motoPurple,
          size: 42,
        ),
        title: const Text('Demo booking created!'),
        content: const Text(
          'Your booking flow is working. No real driver has '
          'been contacted and no payment has been taken. '
          'We will connect this screen to live ride requests '
          'in a later phase.',
        ),
        actions: [
          TextButton(
            onPressed: () {
              Navigator.pop(dialogContext);
              setState(() => showEstimate = false);
            },
            child: const Text('Done'),
          ),
        ],
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    final fare = sampleFares[selectedRide]!;

    return Scaffold(
      appBar: AppBar(
        title: const Text('Book a ride'),
        backgroundColor: motoBackground,
      ),
      body: SafeArea(
        child: ListView(
          padding: const EdgeInsets.all(20),
          children: [
            Container(
              height: 170,
              decoration: BoxDecoration(
                gradient: const LinearGradient(
                  colors: [
                    Color(0xFFEDE6FF),
                    Color(0xFFDCD0FF),
                  ],
                ),
                borderRadius: BorderRadius.circular(24),
              ),
              child: Stack(
                children: [
                  Positioned(
                    right: 18,
                    top: 18,
                    child: Icon(
                      Icons.location_on_rounded,
                      color: motoPurple.withValues(alpha: 0.3),
                      size: 85,
                    ),
                  ),
                  const Padding(
                    padding: EdgeInsets.all(22),
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      mainAxisAlignment: MainAxisAlignment.center,
                      children: [
                        Icon(
                          Icons.route_rounded,
                          size: 35,
                          color: motoPurple,
                        ),
                        SizedBox(height: 12),
                        Text(
                          'Where to?',
                          style: TextStyle(
                            fontSize: 27,
                            fontWeight: FontWeight.bold,
                            color: motoDark,
                          ),
                        ),
                        SizedBox(height: 5),
                        Text(
                          'Your next journey starts here.',
                          style: TextStyle(color: motoDark),
                        ),
                      ],
                    ),
                  ),
                ],
              ),
            ),
            const SizedBox(height: 26),
            const Text(
              'YOUR JOURNEY',
              style: TextStyle(
                fontWeight: FontWeight.bold,
                letterSpacing: 1.2,
                fontSize: 12,
                color: Colors.black54,
              ),
            ),
            const SizedBox(height: 14),
            TextField(
              controller: pickupController,
              textInputAction: TextInputAction.next,
              decoration: InputDecoration(
                labelText: 'Pickup location',
                hintText: 'e.g. GRA, Port Harcourt',
                prefixIcon: const Icon(
                  Icons.my_location_rounded,
                  color: motoPurple,
                ),
                filled: true,
                fillColor: Colors.white,
                border: OutlineInputBorder(
                  borderRadius: BorderRadius.circular(16),
                  borderSide: BorderSide.none,
                ),
              ),
              onChanged: (_) {
                if (showEstimate) {
                  setState(() => showEstimate = false);
                }
              },
            ),
            const SizedBox(height: 14),
            TextField(
              controller: destinationController,
              textInputAction: TextInputAction.done,
              onSubmitted: (_) => calculateEstimate(),
              decoration: InputDecoration(
                labelText: 'Destination',
                hintText: 'e.g. Port Harcourt Airport',
                prefixIcon: const Icon(
                  Icons.location_on_rounded,
                  color: motoPurple,
                ),
                filled: true,
                fillColor: Colors.white,
                border: OutlineInputBorder(
                  borderRadius: BorderRadius.circular(16),
                  borderSide: BorderSide.none,
                ),
              ),
              onChanged: (_) {
                if (showEstimate) {
                  setState(() => showEstimate = false);
                }
              },
            ),
            const SizedBox(height: 26),
            const Text(
              'CHOOSE YOUR RIDE',
              style: TextStyle(
                fontWeight: FontWeight.bold,
                letterSpacing: 1.2,
                fontSize: 12,
                color: Colors.black54,
              ),
            ),
            const SizedBox(height: 14),
            ...sampleFares.entries.map((entry) {
              final isSelected = selectedRide == entry.key;

              IconData rideIcon;
              if (entry.key == 'MoTo XL') {
                rideIcon = Icons.airport_shuttle_rounded;
              } else if (entry.key == 'MoTo Comfort') {
                rideIcon = Icons.directions_car_filled_rounded;
              } else {
                rideIcon = Icons.directions_car_rounded;
              }

              return Padding(
                padding: const EdgeInsets.only(bottom: 10),
                child: Material(
                  color: isSelected
                      ? const Color(0xFFF0EBFF)
                      : Colors.white,
                  borderRadius: BorderRadius.circular(16),
                  child: InkWell(
                    borderRadius: BorderRadius.circular(16),
                    onTap: () {
                      setState(() {
                        selectedRide = entry.key;
                        showEstimate = false;
                      });
                    },
                    child: Container(
                      padding: const EdgeInsets.all(15),
                      decoration: BoxDecoration(
                        borderRadius: BorderRadius.circular(16),
                        border: Border.all(
                          color: isSelected
                              ? motoPurple
                              : const Color(0xFFE9E3F5),
                          width: isSelected ? 2 : 1,
                        ),
                      ),
                      child: Row(
                        children: [
                          Icon(
                            rideIcon,
                            color: motoPurple,
                            size: 34,
                          ),
                          const SizedBox(width: 14),
                          Expanded(
                            child: Column(
                              crossAxisAlignment:
                                  CrossAxisAlignment.start,
                              children: [
                                Text(
                                  entry.key,
                                  style: const TextStyle(
                                    fontWeight: FontWeight.bold,
                                    fontSize: 15,
                                    color: motoDark,
                                  ),
                                ),
                                const SizedBox(height: 4),
                                Text(
                                  entry.key == 'MoTo XL'
                                      ? 'Extra space for your group'
                                      : entry.key == 'MoTo Comfort'
                                          ? 'A more comfortable ride'
                                          : 'Affordable everyday trips',
                                  style: const TextStyle(
                                    fontSize: 12,
                                    color: Colors.black54,
                                  ),
                                ),
                              ],
                            ),
                          ),
                          const SizedBox(width: 8),
                          Text(
                            '₦${entry.value}',
                            style: const TextStyle(
                              fontWeight: FontWeight.bold,
                              color: motoPurple,
                            ),
                          ),
                          const SizedBox(width: 5),
                          Icon(
                            isSelected
                                ? Icons.radio_button_checked
                                : Icons.radio_button_off,
                            color: motoPurple,
                          ),
                        ],
                      ),
                    ),
                  ),
                ),
              );
            }),
            const SizedBox(height: 12),
            FilledButton.icon(
              onPressed: calculateEstimate,
              icon: const Icon(Icons.receipt_long_rounded),
              label: const Text('Calculate estimated fare'),
              style: FilledButton.styleFrom(
                backgroundColor: motoPurple,
                padding: const EdgeInsets.symmetric(vertical: 17),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(16),
                ),
              ),
            ),
            if (showEstimate) ...[
              const SizedBox(height: 22),
              Container(
                padding: const EdgeInsets.all(20),
                decoration: BoxDecoration(
                  color: Colors.white,
                  borderRadius: BorderRadius.circular(20),
                  border: Border.all(
                    color: const Color(0xFFE9E3F5),
                  ),
                ),
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    const Text(
                      'YOUR DEMO TRIP ESTIMATE',
                      style: TextStyle(
                        fontSize: 12,
                        letterSpacing: 1,
                        fontWeight: FontWeight.bold,
                        color: Colors.black54,
                      ),
                    ),
                    const SizedBox(height: 16),
                    Text(
                      '${pickupController.text.trim()}  →',
                      style: const TextStyle(
                        fontWeight: FontWeight.w600,
                      ),
                    ),
                    Padding(
                      padding: const EdgeInsets.only(left: 8),
                      child: Text(
                        destinationController.text.trim(),
                        style: const TextStyle(
                          color: Colors.black54,
                        ),
                      ),
                    ),
                    const Divider(height: 28),
                    Row(
                      mainAxisAlignment:
                          MainAxisAlignment.spaceBetween,
                      children: [
                        const Text('Estimated sample fare'),
                        Text(
                          '₦$fare',
                          style: const TextStyle(
                            color: motoPurple,
                            fontWeight: FontWeight.bold,
                            fontSize: 23,
                          ),
                        ),
                      ],
                    ),
                    const SizedBox(height: 10),
                    const Text(
                      'Demo price only. This is not calculated '
                      'from actual distance or traffic.',
                      style: TextStyle(
                        fontSize: 12,
                        color: Colors.black54,
                      ),
                    ),
                    const SizedBox(height: 18),
                    SizedBox(
                      width: double.infinity,
                      child: FilledButton(
                        onPressed: requestDemoRide,
                        style: FilledButton.styleFrom(
                          backgroundColor: motoPurple,
                          padding: const EdgeInsets.symmetric(
                            vertical: 16,
                          ),
                        ),
                        child: const Text('Request a demo ride'),
                      ),
                    ),
                  ],
                ),
              ),
            ],
            const SizedBox(height: 25),
            const Text(
              'MoTo is currently in development. No real rides '
              'or payments are processed in this demo.',
              textAlign: TextAlign.center,
              style: TextStyle(
                fontSize: 12,
                color: Colors.black54,
              ),
            ),
          ],
        ),
      ),
    );
  }
}

