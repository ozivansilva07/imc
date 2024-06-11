import 'package:flutter/material.dart';

void main() {
  runApp(IMCCalculadoraApp());
}

class IMCCalculadoraApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'IMC ozivan e nara',
      home: IMCCalculadora(),
    );
  }
}

class IMCCalculadora extends StatefulWidget {
  @override
  _IMCCalculadoraState createState() => _IMCCalculadoraState();
}

class _IMCCalculadoraState extends State<IMCCalculadora> {
  TextEditingController heightController = TextEditingController();
  TextEditingController weightController = TextEditingController();
  double imc = 0.0;

  void calcularIMC() {
    double height = double.parse(heightController.text);
    double weight = double.parse(weightController.text);
    double heightInMeters = height / 100;
    setState(() {
      imc = weight / (heightInMeters * heightInMeters);
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('IMC Calculadora'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            TextField(
              controller: heightController,
              keyboardType: TextInputType.number,
              decoration: InputDecoration(
                labelText: 'sua altura',
              ),
            ),
            SizedBox(height: 20),
            TextField(
              controller: weightController,
              keyboardType: TextInputType.number,
              decoration: InputDecoration(
                labelText: 'seu peso',
              ),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: () {
                calcularIMC();
              },
              child: Text('Calcular'),
            ),
            SizedBox(height: 20),
            Text(
              'Seu IMC é: ${imc.toStringAsFixed(2)}',
              style: TextStyle(fontSize: 20),
            ),
          ],
        ),
      ),
    );
  }
}
